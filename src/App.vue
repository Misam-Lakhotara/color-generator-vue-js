<script setup>
import { onMounted } from 'vue';
const FetchData = async () => {
  const response = await fetch('http://localhost:8080/api/colors');
  const data = await response.json();
  console.log(data);
};

onMounted(() => {
  FetchData();
});



</script>

<template>
  <div>
    11
  </div>
</template>