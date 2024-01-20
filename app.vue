<template>
  <div> {{ data }} </div>
</template>

<script setup>
  let { data } = await useFetch('/api/foo')
</script>