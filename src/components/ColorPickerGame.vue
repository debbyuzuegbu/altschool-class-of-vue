<template>
  <div>
  <h1>Color Picker Game</h1>
  <div class="body" :style="{'background-color': background}">
  <div>{{ res }}</div>
  </div>
  <div class="buttons">
  <button v-for="color in colors" :key="color" @click="match(color)">
  {{ color }}
  </button>
  </div>
  </div>
  </template>
  
  <script>
  import { matchColor } from "../composables/UseColorPicker";
  import { ref } from "vue";
  export default {
  setup() {
  const colors = ["red", "green", "blue", "purple"];
  let res = ref("Pick a color...");
  let background = ref('');
  const match = (color) => {
  let { message, messageColor } = matchColor(color, colors);
  background.value = messageColor
  res.value = message;
  };
  return { res, match, colors, background };
  }
  };
  </script>
  
  
  <style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Raleway:ital,wght@0,100;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,400;1,600;1,700;1,800;1,900&display=swap');
  h1 {
    font-family: 'Raleway', sans-serif;
    font-size: 700;
  }
  .body {
  display: flex;
  width: 400px;
  justify-content: center;
  align-items: center;
  min-height: 60px;
  color: white;
  background-color: grey;
  border-radius: 20px;
  margin: 10px;
  }
  
  .buttons {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  }
</style>
  