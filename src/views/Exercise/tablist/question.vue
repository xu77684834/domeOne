<template>
  <div>
    <p id="topls">
      <van-search
        v-model="value"
        shape="round"
        background="white"
        placeholder="请输入搜索关键词"
        @focus="tozhis"
      >
      </van-search>
    </p>
    <div id="tly_bigbox">
      <div id="tly_leftbox">
        <van-sidebar v-model="activeKey">
          <van-sidebar-item
            v-for="(item, index) in alllist"
            :key="index"
            :title="item.name"
            @click="change(item.id)"
          />
        </van-sidebar>
      </div>
      <div id="tly_rightbox">
        <div v-for="(item, index) in showlist" :key="index">
          <p class="tly_title">{{ item.name }}</p>
          <div class="tly_titlebox" v-show="item.bank != ''">
            <span v-for="(items,index) in item.bank" :key="index" @click="tothis(item.id, items.id)">{{
              items.name
            }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { Sidebar, SidebarItem } from "vant";
import { Search } from "vant";

Vue.use(Search);
Vue.use(Sidebar);
Vue.use(SidebarItem);
export default {
  data() {
    return {
      activeKey: -1,
      showlist: [],
      value: "",
      alllist: []
    };
  },
  mounted() {
    this.$store.commit("changeleftarrows", true)
    this.quest()
    // console.log(this.alllist);
    localStorage.removeItem("showlist")
  },
  methods: {
    async change(id){
      // console.log(id);
      let { data } = await this.$Axios.get('/api/app/wap/quesBank/'+id)
      // console.log(data);
      this.showlist=data.data
    },
    onSearch() {
      console.log(1111);
    },
    tothis(item,title) {
      // console.log(item,title);
      window.localStorage.setItem("thisname", title);
      this.$router.push({
        path: "/footer/Myexercise/showclass",
        query: { name:"/"+item+"/"+title },
      });
    },
    async quest(){
      let { data } = await this.$Axios.get('/api/app/wap/classify')
      // console.log(data);
      this.alllist=data.data
    },
    tozhis(){
      this.$router.push("/footer/Myexercise/seek")
    }
  },
};
</script>
<style lang="scss" scoped>
* {
  margin: 0;
  padding: 0;
}
#topls {
  height: 8vh;
  display: flex;
  align-items: center;
  justify-content: center;
  .van-search{
    width: 80%;
  }
}
#tly_bigbox {
  width: 100%;
  height: 70vh;
  display: flex;
  #tly_leftbox {
    height: 70vh;
    flex: 1;
    background: gainsboro;
    .van-sidebar {
      height: 100%;
      .van-sidebar-item {
        height: 0.5rem;
        display: flex;
        align-items: center;
        justify-content: center;
      }
    }
  }
  #tly_rightbox {
    height: 75vh;
    flex: 4;
    .tly_title {
      color: rgb(139, 138, 138);
      margin: 0.07rem;
    }
    .tly_titlebox {
      width: 100%;
      display: flex;
      box-sizing: border-box;
      padding: 0.05rem;
      span {
        background: rgb(173, 173, 173);
        padding: 0.05rem 0.1rem ;
        color: white;
        font-size: 0.06rem;
        border-radius: 0.05rem;
      }
    }
  }
}
</style>