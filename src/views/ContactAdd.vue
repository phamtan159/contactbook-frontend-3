<template>
  <div class="page">
    <h4>Thêm mới Liên hệ</h4>
    <ContactForm
      :contact="contact"
      @submit:contact="createContact"
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
  data() {
    return {
      contact: {
        name: "",
        email: "",
        address: "",
        phone: "",
        favorite: false,
      },
      message: "",
    };
  },
  methods: {
    // Xử lý thêm mới thông tin liên hệ
    async createContact(data) {
      try {
        await ContactService.create(data);
        this.message = "Liên hệ được thêm mới thành công.";
        setTimeout(() => {
          this.$router.push({ name: "contactbook" });
        }, 1000);
      } catch (error) {
        console.log(error);
        this.message = "Có lỗi xảy ra khi thêm mới liên hệ.";
      }
    },
  },
};
</script>

<style scoped>
.page {
  text-align: left;
  max-width: 750px;
}
</style>
