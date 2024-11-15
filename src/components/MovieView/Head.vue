<template>
<div class="head">
    <div class="title">{{ title }}</div>
    <div class="more">More</div>
  </div>
</template>
<script setup>
import { defineProps } from 'vue';
const props = defineProps({
  title: {
    type: String
  }
})
</script>
<style >
  .head {
    display: flex;
    align-items: flex-end;
    justify-content: space-between;
    width: 80%;
    margin-left:auto;
    margin-right:auto;
    padding: 35px 15px 0 15px;
  }
.title {
    font-size: 28px;
    font-weight: 900;
  }

  .more {
    color: rgb(104, 147, 187);
  }
</style>
