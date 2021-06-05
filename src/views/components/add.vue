<template>
  <div class="add">
    <div class="add__inner">
      <input
        class="add__input"
        type="text"
        placeholder="todo's..."
        v-model="newTodoItem"
      >
      <button
        type="button"
        class="add__button"
        @click="addToItem"
        @keyup.enter="addToItem"
      >
      </button>
    </div>
  </div>
</template>

<script>
export default {
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
  &__inner {
    background-color: #fff;
    border-radius: 20px;
    box-shadow: -2px -2px 5px rgba($color: #f5f5f5, $alpha: 1.0), 3px 3px 5px rgba(0, 0, 0, 0.1);
    position: relative;
  }
  &__input {
    padding: 20px 40px 20px 10px;
    width: 100%;
    height: 100%;
    font-size: 14px;
    color: #333;
    display: block;
  }
  &__button {
    position: absolute;
    top: 29px;
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
