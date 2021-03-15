<template>
  <header class="header">
    <div class="header__inner">
      <h1 class="header__title">
        Todo's
      </h1>
      <span class="header__date">{{ timestamp }}</span>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      timestamp: ''
    };
  },
  created() {
    const current = new Date();
    const month = current.getMonth() + 1;
    const date = current.getDate();
    const weekList = new Array('일', '월', '화', '수', '목', '금', '토');
    const week = weekList[current.getDay()];
    this.timestamp = `${month}/${date} ${week}`
  }
}
</script>

<style lang="scss" scoped>
.header {
  width: 100%;
  height: 70px;
  // background: #006ea6;
  background: linear-gradient(10deg, rgba(0,110,166,1) 0%, rgba(52,152,219,1) 50%, rgba(0,212,255,1) 100%);
  &__inner {
    padding: 0 12px;
    height: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  &__title {
    font-size: 14px;
    color: #fff;
    font-weight: 700;
    text-align: center;
  }
  &__date {
    font-size: 14px;
    color: #fff;
    font-weight: 700;
  }
}
</style>
