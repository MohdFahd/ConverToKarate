<script setup>
import HelloWorld from "./components/HelloWorld.vue";
</script>

<template>
  <div style="display: flex; justify-content: center; align-items: center">
    <div>
      <div>
        <img
          src="https://www.kloia.com/hubfs/karate-framework.png"
          width="20%"
          alt=""
        />
      </div>
      <div style="font-size: 30px; margin: 10px 0px">Karate Convertor</div>
    </div>
  </div>
  <HelloWorld msg="Vite + Vue" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
