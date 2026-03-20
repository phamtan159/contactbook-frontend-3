<script>
export default {
  props: {
    // Giá trị nhận từ v-model của component cha
    modelValue: { type: String, default: "" },
  },
  // Khai báo các sự kiện mà component này sẽ phát ra
  emits: ["submit", "update:modelValue"],
  methods: {
    // Cập nhật giá trị khi người dùng nhập liệu
    updateModelValue(e) {
      this.$emit("update:modelValue", e.target.value);
    },
    // Phát sự kiện khi nhấn nút Tìm kiếm hoặc phím Enter
    submit() {
      this.$emit("submit");
    },
  },
};
</script>

<template>
  <div class="input-group">
    <input
      type="text"
      class="form-control"
      placeholder="Nhập thông tin cần tìm"
      :value="modelValue"
      @input="updateModelValue"
      @keyup.enter="submit"
    />
    <div class="input-group-append">
      <button
        class="btn btn-outline-secondary"
        type="button"
        @click="submit"
      >
        <i class="fas fa-search"></i> Tìm kiếm
      </button>
    </div>
  </div>
</template>

