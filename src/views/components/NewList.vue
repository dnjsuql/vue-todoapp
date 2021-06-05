<template>
  <ul>
    <li
      v-for="item in logdata"
      :key="item.itemz"
    >
      <p> {{ item.itemz }} </p>
    </li>
  </ul>
</template>

<script>
export default {
  props: ['logdata'],
  data(){
    return {
      
    }
  }
}
</script>

<style>

</style>