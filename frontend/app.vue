<template>
  <div> {{ greet }} </div>
</template>

<script setup>
const url =  'http://localhost:1337/api/greeting';

let greet = ref('')

fetch(url)
  .then(response => {
    if (!response.ok) {
      throw new Error(`Network response was not ok: ${response.statusText}`);
    }
    return response.json();
  })
  .then(data => {
    greet.value =  data.data.attributes.greeting
  })
  .catch(error => {
    console.error('Error:', error.message);
  });

onMounted(() => {
  fetch(url);
})
</script>