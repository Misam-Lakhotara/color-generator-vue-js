<script setup>
import { ref } from "vue";
const color = ref("bg-gray-500");

const changeColor = (newColor) => {
  color.value = newColor;
};
const getRandomColor = () => {
  const colors = [
    "bg-red-500",
    "bg-green-500",
    "bg-blue-500",
    "bg-yellow-500",
    "bg-purple-500",
    "bg-pink-500",
  ];
  return colors[Math.floor(Math.random() * colors.length)];
};
</script>

<template>
  <div class="flex justify-center space-x-5 items-center mt-10 flex-col">
    <div class="flex flex-row">
      <button
        class="box-border border-2 m-5 p-5 bg-red-800 text-white"
        @click="changeColor('bg-red-800')"
      >
        Red
      </button>
      <button
        class="box-border border-2 m-5 p-5 bg-green-800 text-white"
        @click="changeColor('bg-green-800')"
      >
        Green
      </button>
      <button
        class="box-border border-2 m-5 p-5 bg-blue-800 text-white"
        @click="changeColor('bg-blue-800')"
      >
        Blue
      </button>
      <button
        class="box-border border-2 m-5 p-5 bg-slate-100 text-black"
        @click="changeColor(getRandomColor())"
      >
        Random color
      </button>
    </div>

    <div :class="`w-96 h-96 mt-10 ${color}`"></div>
  </div>
</template>
