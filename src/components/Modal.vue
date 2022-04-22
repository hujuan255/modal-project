<template>
  <!-- @clicl.self 事件修饰符只作用在该元素身上的事件，忽略了其他元素的冒泡或捕获事件，这种忽略只局限于自身 -->
  <div class="backrop" @click.stop="closeModal">
    <!-- 动态添加类,类名为sale -->
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <!-- <h1>朋友</h1>
      <P>你好</P> -->
      <h1>{{ header }}</h1>
      <p>{{ text }}</p>
    </div>
  </div>
</template>
<script>
export default {
  props: ["header", "text", "theme"],
  methods: {
    //通过$emit触发父组件的自定义的close事件
    closeModal() {
      this.$emit("close");
    },
  },
};
</script>
<style>
.modal {
  width: 400px;
  padding: 20px;
  margin: 200px auto;
  background: #fff;
  border-radius: 10px;
}
.backrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
}
.modal h1 {
  color: aquamarine;
  border: none;
  padding: 0;
}
.modal.sale {
  background: #e33434;
  color: #fff;
}
.modal.sale h1 {
  color: #fff;
}
</style>