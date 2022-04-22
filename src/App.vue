<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name" />
  <button @click="handleClick">点击</button>
  <div v-if="isShowModal">
    <!-- 自定义事件close
    <Modal
      :header="header"
      :text="text"
      theme="sale"
      @close="toggleModal"
    ></Modal> -->
    <!-- 插槽 slot -->
    <Modal theme="sale" @close="toggleModal">
      <!-- 具名插槽 在template元素上使用v-slot指令，以v-slot的值为其提供名称-->
      <template v-slot:links>
        <a href="https://www.baidu.com">百度</a>
        <a href="https://www.sina.com">新浪</a>
      </template>
      <h1>引爆点</h1>
      <p>如何引发流行?</p>
    </Modal>
  </div>
  <teleport to=".modals" v-if="isShowModal2">
    <Modal @close="toggleModal2">
      <p>这是一个插槽</p>
    </Modal>
  </teleport>
  <!-- 
        默认左键单击
        @click.right 右键
        @click.shift 按住shift单击
        @click.ctrl 按住ctrl单击
        @click.alt 按住alt单击
    -->
  <button @click="toggleModal">显示模板</button>
  <button @click="toggleModal2">显示练习模板</button>
</template>

<script>
import Modal from "./components/Modal.vue";
export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title: "Hello World",
      header: "提示",
      text: "你好",
      isShowModal: false,
      isShowModal2: false,
    };
  },
  methods: {
    handleClick() {
      //获得控件名称
      console.log(this.$refs.name);
      //添加类
      this.$refs.name.classList.add("active");
      //获得焦点
      this.$refs.name.focus();
    },
    toggleModal() {
      this.isShowModal = !this.isShowModal;
    },
    toggleModal2() {
      this.isShowModal2 = !this.isShowModal2;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  padding-bottom: 20px;
  border-bottom: 1px solid #ddd;
}
</style>
