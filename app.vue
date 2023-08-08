<template>
  <main class="main">
    <div style="margin-bottom: 10px">
       
    </div>
    <Code :data="data" />
  </main>
</template>
<script setup>
import { ref } from "vue";
const data = reactive({
  inputValue: "https://interactivesystems.pl/",
  width: 400,
  height: 400,
});
</script>
<style>
.main {
  display: flex;
  justify-content: center;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.input {
  font-size: 18px;
  border-radius: 10px;
  width: 300px;
  height: 30px;
}
</style>
