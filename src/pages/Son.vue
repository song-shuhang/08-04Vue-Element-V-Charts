<template>
  <div>
    我是子组件
    <button @click="son">1231</button>
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    data(){
      return{
        ss:'子组件子组件'
      }
    },
    methods:{
      son(){
        this.$emit('click',this.ss)
      }
    }
  }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">

 
</style>
