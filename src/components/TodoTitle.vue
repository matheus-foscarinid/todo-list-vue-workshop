<template>
  <h3>
    TODO List do {{name}}
  </h3>
</template>

<script setup>
import { ref } from 'vue';

const name = ref('Matheus');
</script>