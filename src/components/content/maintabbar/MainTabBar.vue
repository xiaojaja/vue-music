<template>
  <nav-bar>
    <div slot="left" class="left">
      <router-link tag="div" to="/menu" >menu</router-link>
    </div>
    <div slot="center" class="center">
      <div class="center_item" v-for="(attr,index) in navbar_center" :key="attr"
      @click="itemClick(index)"
      :class="{chooseItem:index==isChoose}" >
      {{attr}}
      </div>
    </div>
    <div slot="right" class="right">
      <router-link tag="div" to="/search" >search</router-link>
    </div>
  </nav-bar>
</template>

<script>
import NavBar from "components/common/navbar/NavBar";
export default {
  name: "MainTabBar",
  components:{
    NavBar
  },
  data(){
    return {
      navbar_center:["我的","发现","云村","视频"],
      path:['/profile','/find','/cloud_village','/video'],
      isChoose:1
    }
  },
  methods:{
    itemClick(index){
      console.log(index)
      this.isChoose = index
      this.$router.push(this.path[index])
    }
  }

}
</script>

<style lang="scss" scoped>
.center{
  display: flex;
  padding: 0 30px;
  font-size: 12px;
  .center_item{
    flex:1;
  }
}

</style>
