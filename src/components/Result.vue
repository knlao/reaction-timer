<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal">
      <h3>Your result</h3>
      <h1>{{ score }} ms</h1>
      <button @click="closeModal">play again</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["score"],
  methods: {
    closeModal() {
      this.$emit("close");
    },
  },
};
</script>

<style>
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}
.modal h1 {
  color: #03cfb4;
  border: none;
  padding: 0;
}
</style>
