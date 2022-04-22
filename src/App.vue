<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name" />
  <button @click="handleClick">点击</button>
  <div v-if="isShowModal">
    <!-- 自定义事件close -->
    <Modal
      :header="header"
      :text="text"
      theme="sale"
      @close="toggleModal"
    ></Modal>
  </div>
  <!-- 
        默认左键单击
        @click.right 右键
        @click.shift 按住shift单击
        @click.ctrl 按住ctrl单击
        @click.alt 按住alt单击
    -->
  <button @click="toggleModal">显示模板</button>
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
