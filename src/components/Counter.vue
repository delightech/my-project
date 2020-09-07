<template>
  <div class="counter">
    <p>{{ name }}</p>
    <p>Count: {{ count }}</p>
    <button @click="increment">+1</button>
  </div>
</template>

<script>
export default {
  // porpsは親コンポーネントから渡される値が代入される
  // コンポーネント内で書き換えはできない
  props: {
    name: String,
    initCount: Number
  },
  // data()はコンポーネントのマウント時に一度だけ行われる
  data() {
    return {
      count: this.initCount
    }
  },
  methods: {
    increment() {
      this.count++;
      this.$emit("emitUp", {name: this.name, counted: this.count})
    }
  }
}
</script>

<style lang="scss" scoped>
.counter {
  //width: 200px;
}
</style>
