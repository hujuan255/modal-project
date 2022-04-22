<template>
  <!-- @clicl.self 事件修饰符只作用在该元素身上的事件，忽略了其他元素的冒泡或捕获事件，这种忽略只局限于自身 -->
  <div class="backrop" @click.self="closeModal">
    <!-- 动态添加类,类名为sale -->
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <!-- props -->
      <!-- <h1>朋友</h1>
      <P>你好</P> -->
      <!-- <h1>{{ header }}</h1>
      <p>{{ text }}</p> -->
      <!-- 默认插槽 slot -->
      <slot></slot>
      <!-- 具名插槽，名称为links的template元素中的所有内容都将会被传入本插槽中 -->
      <div class="actions">
        <slot name="links"></slot>
      </div>
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
.modal .actiocs {
  text-align: center;
  margin: 30px 0 10px 0;
}
.modal .actions a {
  color: #333;
  padding: 8px;
  border: 1px solid #eee;
  border-radius: 5px;
  text-decoration: none;
  margin: 10px;
}
.modal.sale {
  background: #e33434;
  color: #fff;
}
.modal.sale h1 {
  color: #fff;
}
.modal.sale .actions {
  color: #fff;
}
.modal.sale .actions a {
  color: #fff;
}
</style>