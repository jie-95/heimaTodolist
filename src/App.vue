<template>
  <div class="todoapp">
    <MyHeader @addTask="addFn"/>
    <MyMain :list="list" @del="delFn" />
    <MyFooter :count="countFn"/>
  </div>
</template>

<script>
import MyHeader from "./components/MyHeader";
import MyMain from "./components/MyMain";
import MyFooter from "./components/MyFooter";
export default {
   data() {
    return {
      list: [
        { id: 100, name: "吃饭", isDone: true },
        { id: 101, name: "睡觉", isDone: false },
        { id: 102, name: "打豆豆", isDone: true },
      ],
    };
  },
  components: {
    MyHeader,
    MyMain,
    MyFooter,
  },
  methods:{
    addFn(val){
      // console.log(val);
      this.list.push({
        name:val,
        isDone:false,
        id:(this.list.length? this.list[this.list.length-1].id + 1: 100)
      })
    },
    delFn(val){
      console.log(val);
      const index = this.list.findIndex((ele) => ele.id == val)
      console.log(index);
      this.list.splice('index',1)
    }
  },
  computed:{
    countFn(){
      console.log(this.list.filter((ele) => !ele.isDone).length);
     return this.list.filter((ele) => !ele.isDone).length
    }
  }
};
</script>

<style>
</style>