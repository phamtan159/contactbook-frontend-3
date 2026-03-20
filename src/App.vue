<script>
import AppHeader from "@/components/AppHeader.vue";

export default {
  components: {
    AppHeader,
  },
};
</script>

<template>
  <div id="app">
    <AppHeader />

    <div class="container mt-3">
      <router-view />
    </div>
  </div>
</template>

<style>
/* Style dùng chung cho toàn bộ ứng dụng */
.page {
  max-width: 400px;
  margin: auto;
}

/* Bạn có thể thêm các định dạng bổ sung cho container tại đây */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>