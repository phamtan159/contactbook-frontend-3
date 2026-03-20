<script>
export default {
  props: {
    // Danh sách các liên hệ truyền từ component cha
    contacts: { type: Array, default: () => [] },
    // Chỉ số của liên hệ đang được chọn
    activeIndex: { type: Number, default: -1 },
  },
  // Khai báo sự kiện để cập nhật lại chỉ số đang hoạt động cho cha
  emits: ["update:activeIndex"],
  methods: {
    updateActiveIndex(index) {
      this.$emit("update:activeIndex", index);
    },
  },
};
</script>

<template>
  <ul class="list-group">
    <li
      v-for="(contact, index) in contacts"
      :key="contact._id"
      class="list-group-item"
      :class="{ active: index === activeIndex }"
      @click="updateActiveIndex(index)"
    >
      {{ contact.name }}
    </li>
  </ul>
</template>

<style scoped>
.list-group-item {
  cursor: pointer;
}
.list-group-item.active {
  color: #fff;
  background-color: #007bff;
}
</style>