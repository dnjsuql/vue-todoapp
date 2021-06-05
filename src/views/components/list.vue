<template>
  <ul class="list">
    <li class="list__item"
      v-for="(todoItem, index) in propsdata"
      v-bind:key="todoItem.item"
    >
      <input
        type="checkbox"
        class="list__checkbox"
        v-bind:id="todoItem.item"
      >
      <label
        v-bind:for="todoItem.item"
        class="list__label"
      >
        <p class="list__text">{{ todoItem.item }}</p>
      </label>
      <!-- <span class="list__date">5/26</span> -->
      <button type="button" class="list__delete" @click="removeTodo(todoItem, index)"></button>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'List',
  props: ['propsdata'],
  methods: {
    removeTodo(todoItem, index) {
      this.$emit("removeItem", todoItem, index);
    }
  }
}
</script>

<style lang="scss" scoped>
.list {
  margin-top: 40px;
  &__item {
    padding: 16px 32px;
    width: 100%;
    min-height: 50px;
    background-color: #fff;
    position: relative;
    box-shadow: 3px 3px 9px -1px rgba(153,153,153,0.75);
    & + & {
      margin-top: 10px;
    }
  }
  &__label {
    display: block;
  }
  &__text {
    height: 100%;
    font-size: 14px;
    color: #666;
  }
  &__checkbox {
    position: absolute;
    top: 50%;
    left: 8px;
    transform: translateY(-50%);
    margin: 0;
    border: 1px solid #ccc;
    width: 16px;
    height: 16px;
    background-color: #fff;
    appearance: auto;
  }
  &__date {
    position: absolute;
    bottom: 8px;
    right: 8px;
    font-size: 10px;
  }
  &__delete {
    position: absolute;
    top: 50%;
    right: 8px;
    width: 16px;
    height: 16px;
    font-size: 12px;
    transform: translateY(-50%);
    &:after {
      content: '';
      position: absolute;
      top: 50%;
      left: 50%;
      width: 2px;
      height: 12px;
      transform: translate(-50%, -50%) rotate(45deg);
      background-color: #999;
    }
    &:before {
      content: '';
      position: absolute;
      top: 50%;
      left: 50%;
      width: 2px;
      height: 12px;
      transform: translate(-50%, -50%) rotate(-45deg);
      background-color: #999;
    }
  }
}
</style>
