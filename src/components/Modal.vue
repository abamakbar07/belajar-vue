<template>
  <div class="backdrop" @click.self="close">
    <div class="modal" :class="{ active: isActive === 'active' }">
      <slot></slot>
      <div class="spesificTemplate">
        <slot name="button"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: ["isActive"],
  methods: {
    close() {
      this.$emit("close");
    }
  }
};
</script>

<style>
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}
.modal {
  text-align: center;
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}
.modal h1 {
  color: blue;
}
.modal.active h1 {
  color: white;
}
.modal.active {
  background: blueviolet;
  color: white;
}
</style>
