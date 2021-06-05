<template>
  <div>
    <button type="button" class="button">
      {{ title }}
    </button>
  </div>
</template>

<script>
export default {
  data(){
    return {
      title: ''
    }
  },
  // props: ['title']
}
</script>

<style scoped>
.button {
  width: 50px;
  height: 30px;
  background-color: #fff;
  border: 1px solid #ccc;
  color: blue;
}
</style>