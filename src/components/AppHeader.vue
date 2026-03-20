<template>
  <nav class="navbar navbar-expand navbar-dark bg-dark">
    <a href="/" class="navbar-brand">Ứng dụng Quản lý danh bạ</a>

    <div class="mr-auto navbar-nav">
      <li class="nav-item">
        <router-link :to="{ name: 'contactbook' }" class="nav-link">
          Danh bạ
          <i class="fas fa-address-book"></i>
        </router-link>
      </li>
    </div>
  </nav>
</template>

<script>
export default {
  // Component này hiện tại chỉ hiển thị giao diện tĩnh nên không cần logic phức tạp
};
</script>

<style scoped>
/* Tùy chỉnh thêm khoảng cách hoặc màu sắc cho các liên hệ nếu cần */
.navbar-brand {
  font-weight: bold;
}
.nav-link i {
  margin-left: 5px;
}
</style>