<template>
  <div class="list-box">
    <Header/>
    <Main/>
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import Main from "@/components/Main.vue";

export default {
  components: {
    Header,
    Main
  }
}
</script>

<style>
.list-box {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 80%;
  height: 90%;
  padding: 40px;
  transform: translate(-50%, -50%);
  background: var(--card-color);
  box-sizing: border-box;
  box-shadow: 0 15px 25px #00000099;
}
</style>