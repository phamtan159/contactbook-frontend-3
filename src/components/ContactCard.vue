<script>
export default {
  props: {
    // Đối tượng liên hệ bắt buộc phải có để hiển thị
    contact: { type: Object, required: true },
  },
};
</script>

<template>
  <div class="contact-card">
    <div class="p-1">
      <strong>Tên:</strong>
      {{ contact.name }}
    </div>
    <div class="p-1">
      <strong>E-mail:</strong>
      {{ contact.email }}
    </div>
    <div class="p-1">
      <strong>Địa chỉ:</strong>
      {{ contact.address }}
    </div>
    <div class="p-1">
      <strong>Điện thoại:</strong>
      {{ contact.phone }}
    </div>
    <div class="p-1">
      <strong>Liên hệ yêu thích:&nbsp;</strong>
      <i v-if="contact.favorite" class="fas fa-check text-success"></i>
      <i v-else class="fas fa-times text-danger"></i>
    </div>
  </div>
</template>

<style scoped>
.contact-card {
  line-height: 1.6;
}
/* Thêm màu sắc cho icon để dễ phân biệt */
.text-success { color: #28a745; }
.text-danger { color: #dc3545; }
</style>