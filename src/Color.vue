<script lang="ts" setup>
import { onMounted, ref } from "vue";

const colors = ref([]);
const selectedColor = ref("");
const isFetching = ref(true);

const changeColor = (newColor) => {
  selectedColor.value = newColor;
};

onMounted(() => {
  fetchColors();
});

const fetchColors = async () => {
  const response = await fetch("http://localhost:8080/api/colors");
  const data = await response.json();
  colors.value = data.colors;
  selectedColor.value = colors.value[0]?.value;
  isFetching.value = false;
};
</script>

<template>
  <div class="flex justify-center space-x-5 items-center mt-10 flex-col">
    <div v-if="isFetching">
      <p>Loading...</p>
    </div>
    <div v-else-if="colors.length === 0">
      <p>Please add colors</p>
    </div>
    <template v-else>
      <div class="flex flex-row">
        <button
          v-for="(color, index) in colors"
          :key="index"
          class="box-border m-5 p-5 text-white rounded-md"
          :style="{ 'background-color': color.value }"
          @click="changeColor(color.value)"
        >
          {{ color?.label }}
        </button>
      </div>

      <div
        :class="`w-96 h-96 mt-10 box-border rounded-sm`"
        :style="{ 'background-color': selectedColor }"
      />
    </template>
  </div>
</template>
