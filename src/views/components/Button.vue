<template>
  <div>
    <input
      type="text"
      class="testInput"
      v-model="loging"
    >
    <button
      type="button"
      class="button"
      @click="clickLog"
    >
      버튼
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loging: ''
    }
  },
  methods: {
    clickLog(){
      if(this.loging !== ''){
        this.$emit('clickLogCheck', this.loging);
        this.loging = '';
      }
    }
  }
}
</script>

<style scoped>
.button {
  width: 50px;
  height: 30px;
  background-color: #fff;
  border: 1px solid #ccc;
  color: red;
}
.testInput {
  margin-top: 10px;
  padding: 10px;
  border: 3px solid #000;
  width: 100%;
  background-color: #fff;
}
</style>