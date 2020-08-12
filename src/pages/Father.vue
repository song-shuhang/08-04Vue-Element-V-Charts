<template>
  <div>
    我是父组件
    <div id="box">{{msg}}</div>

     <button @click="go">点餐</button>
     <hr/><hr/>
    <p>{{lis.toString()}}</p>
   
    <hr/><hr/>
    <son @click="btn">126</son>
  </div>
</template>

<script type="text/ecmascript-6">
import son from "./Son.vue";
  export default {
    data(){
      return{
        msg:'',
        lis:[
          "黄焖鸡","粥","水果-酸奶","麻辣烫","米线","炒饼","蛋炒饭","煎饼果子","面条",
        ],
      }
    },
    methods:{
      btn(ss){
        console.log("我是子组件传来的"+ ss)
      },
      go(){
        console.log(new Date())
        console.log(this.lis)
       this.msg =''
      const  that = this.lis
      // console.log
        // console.log(that)
      //  this.msg.push(Math.ceil(Math.random()*this.lis)) 
      // console.log(Math.ceil(Math.random()*that.length))
      const lisindex = Math.floor(Math.random()*that.length)
      this.msg = that[lisindex].toString()
      // this.msg.push(that[lisindex])  
       
      }
    },
    components:{
      son
    }
  }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
#box
  width 200px
  height 30px
  border-bottom 1px solid #cccccc
  text-align center
  line-height 30px
</style>
