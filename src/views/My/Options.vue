<template>
  <div id="app">
    <van-nav-bar title="设置" left-text  left-arrow @click-left="onClickLeft"  />
    <!-- 设置密码 -->
    <ul>
      <li @click="$router.push('/goPass')" >
          <!-- ::before -->
          设置密码</li>
    </ul>
    <div class="bottom-box">
      <div class="btn-exit" @click="clear">
        退出登录
      </div>
    </div>
  </div>
</template>


<script>
export default {
  // 组件名称
  name: "",
  // 组件参数 接收来自父组件的数据
  props: [],
  // 局部注册的组件
  components: {  },
  // 组件状态值
  data() {
    return {};
  },
  // 计算属性
  computed: {},
  // 侦听器
  watch: {},
  // 组件方法
  methods: {
    clear(){
      sessionStorage.clear()
      this.$store.state.act = 0
      this.$router.push('/footer/myhome')
    },
    onClickLeft() {
      this.$router.go(-1);
    },
  },
  /**
   * 组件实例创建完成，属性已绑定，但DOM还未生成，$ el属性还不存在
   */
  created() {},
  mounted() {}
};
</script> 


<style scoped lang="scss">
ul {
  margin-bottom: 0;
  background: #fff;
  padding: 1.3vw 4vw;
  margin: 2vw 0 0;
}
li {
  height: 14.66667vw;
  line-height: 14.66667vw;
  position: relative;
  font-size: 3.73333vw;
  color: #595959;
}
.bottom-box {
  overflow: hidden;
  background-color: #fff;
  height: 4rem;
  height: 40vw;
}
.btn-exit {
background-color: #eb6100;
    color: #fff;
    width: 9.2rem;
    width: 92vw;
    height: 11.73333vw;
    margin: 17.33333vw auto;
    border-radius: 1.06667vw;
    font-size: 4.53333vw;
    text-align: center;
    line-height: 11.73333vw;
}
::before{
    content: "";
    display: block;
    position: absolute;
    right: 0;
    top: 50%;
    transform: translateY(-50%) rotate(45deg);
    width: 2.66667vw;
    height: 2.66667vw;
    border-top: 1px solid #b7b7b7;
    border-right: 1px solid #b7b7b7;
}
#app {
  background: #fff;
  min-height: 100vh;
  box-sizing: border-box;
}
</style>
