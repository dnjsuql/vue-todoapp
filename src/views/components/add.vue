<template>
  <div class="add">
    <input
      class="add__input"
      type="text"
      placeholder="todo's..."
      v-model="newTodoItem"
    >
    <button
      type="button"
      class="add__button"
      aria-label="투두 추가하기"
      @click="addToItem"
    >
    </button>
  </div>
</template>

<script>
export default {
  name: 'add',
  data() {
    return {
      newTodoItem: ''
    };
  },
  methods: {
    addToItem() {
      if(this.newTodoItem !== '') {
        this.$emit("addItem", this.newTodoItem);
        this.clearInput();
      }
    },
    clearInput() {
      this.newTodoItem = '';
    }
  }
}
</script>

<style lang="scss" scoped>
.add {
  margin-top: 20px;
  width: 100%;
  position: relative;
  &__input {
    padding: 10px 40px 10px 10px;
    border: 1px solid #999;
    width: 100%;
    height: 100%;
    background-color: #fff;
    font-size: 14px;
    color: #333;
    display: block;
  }
  &__button {
    position: absolute;
    top: 19px;
    right: 0;
    transform: translate(-50%, -50%);
    width: 20px;
    height: 20px;
    border-radius: 50%;
    border: 1px solid #999;
    &:after {
      content: '';
      position: absolute;
      top: 50%;
      right: 4px;
      border-top: 1px solid #999;
      border-right: 1px solid #999;
      width: 6px;
      height: 6px;
      transform: translate(-50%, -50%) rotate(45deg);
    }
  }
}
</style>
