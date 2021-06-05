<template>
  <div class="backdrop">
    <div class="modal">
      <h1>{{ modalData.title }}</h1>
      <p>{{ text }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: ["modalData", "text"]
  // methods: {
  //   getData() {
  //     console.log(this.modalData);
  //   }
  // }
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
</style>
