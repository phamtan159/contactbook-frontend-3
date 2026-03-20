<template>
  <div v-if="contact" class="page">
    <h4>Hiệu chỉnh Liên hệ</h4>
    <ContactForm
      :contact="contact"
      @submit:contact="updateContact"
      @delete:contact="deleteContact"
    />
    <p class="mt-3 text-info">{{ message }}</p>
  </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";

export default {
  components: {
    ContactForm,
  },
  props: {
    // ID được truyền từ Vue Router thông qua props: true
    id: { type: String, required: true },
  },
  data() {
    return {
      contact: null,
      message: "",
    };
  },
  methods: {
    // Lấy thông tin chi tiết của một liên hệ để đổ vào form
    async getContact(id) {
      try {
        this.contact = await ContactService.get(id);
      } catch (error) {
        console.log(error);
        // Nếu không tìm thấy ID, đẩy người dùng sang trang 404
        this.$router.push({
          name: "notfound",
          params: {
            pathMatch: this.$route.path.split("/").slice(1),
          },
          query: this.$route.query,
          hash: this.$route.hash,
        });
      }
    },

    // Xử lý cập nhật thông tin liên hệ
    async updateContact(data) {
      try {
        await ContactService.update(this.contact._id, data);
        this.message = "Liên hệ được cập nhật thành công.";
        // Thêm một chút delay hoặc dùng thông báo trước khi chuyển trang
        setTimeout(() => {
          this.$router.push({ name: "contactbook" });
        }, 1000);
      } catch (error) {
        console.log(error);
      }
    },

    // Xử lý xóa liên hệ đang chọn
    async deleteContact() {
      if (confirm("Bạn muốn xóa Liên hệ này?")) {
        try {
          await ContactService.delete(this.contact._id);
          this.$router.push({ name: "contactbook" });
        } catch (error) {
          console.log(error);
        }
      }
    },
  },
  created() {
    // Ngay khi trang được khởi tạo, gọi API lấy dữ liệu
    this.getContact(this.id);
    this.message = "";
  },
};
</script>

<style scoped>
.page {
  text-align: left;
  max-width: 750px;
}
</style>