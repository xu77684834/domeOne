<template>
  <div>
    <van-nav-bar
      title="学习日历"
      left-arrow
      @click-left="onClickLeft"
    />
    <van-calendar
      title=""
      
      :poppable="false"
      :show-confirm="false"
      :style="{ height: '400px' }"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      
    };
  },
  methods: {
    onClickLeft(){
      this.$router.go(-1)
    }
  }
};
</script>

<style scoped>
.coach_head {
  width: 100%;
  height: 0.5rem;
  background: rgb(240, 242, 245);
  display: flex;
  justify-content: center;
}
.coach_head_top img {
  width: 0.3rem;
  height: 0.3rem;
  margin-left: -1.3rem;
  margin-top: 0.1rem;
}
.coach_head_text {
  float: left;
  height: 0.5rem;
  line-height: 0.5rem;
}
.coach_head_reght {
  width: 0.3rem;
  height: 0.5rem;
  float: right;
}
.coach_head_reght img {
  width: 0.3rem;
  height: 0.3rem;
  margin-left: 1.3rem;
  margin-top: 0.1rem;
}
</style>