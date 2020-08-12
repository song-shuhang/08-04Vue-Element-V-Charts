<template>
  <div id="box">
    <header id="box-header"> 
      <div class="header-lfet">我是首页</div>
      <ul class="header-right">
        <li>             
          <p >{{nowTime}}</p>  
          <p > {{nowDate}}</p>        
        </li>
        <li>
          <p>{{nowWeek}}</p>
          <p>天气</p>
        </li>       
      </ul>
    </header>
  </div>
</template>

<script type="text/ecmascript-6">
  // var myDate = new Date(); 
  export default {
    data(){
      return{
         nowDate: "",    // 当前日期
         nowTime: "",    // 当前时间
         nowWeek: ""     // 当前星期
                
      }
    },
    methods:{
         currentTime() {
            setInterval(this.getDate, 500);
        },
        getDate: function() {
            var _this = this;
            let yy = new Date().getFullYear();
            let mm = new Date().getMonth() < 10
                    ? "0" + (new Date().getMonth()+ 1)
                    : (new Date().getMonth()+ 1 );//获取当前月份(0-59)
            let dd = new Date().getDate();
            let week = new Date().getDay();
            let hh = new Date().getHours()< 10
                    ? "0" + new Date().getHours()
                    : new Date().getHours();//获取当前小时数(0-59)
            let ss = new Date().getSeconds()< 10
                    ? "0" + new Date().getSeconds()
                    : new Date().getSeconds(); //获取当前秒数(0-59)
            let mf =
                new Date().getMinutes() < 10
                    ? "0" + new Date().getMinutes()
                    : new Date().getMinutes();//获取当前分钟数(0-59)
            if (week == 1) {
                this.nowWeek = "星期一";
            } else if (week == 2) {
                this.nowWeek = "星期二";
            } else if (week == 3) {
                this.nowWeek = "星期三";
            } else if (week == 4) {
                this.nowWeek = "星期四";
            } else if (week == 5) {
                this.nowWeek = "星期五";
            } else if (week == 6) {
                this.nowWeek = "星期六";
            } else {
                this.nowWeek = "星期日";
            }
            _this.nowTime = hh + ":" + mf +":"+ss;
            _this.nowDate = yy + "/" + mm + "/" + dd;
        }
    },
    
    mounted(){
      // setchange()
      // this.myDate = new Date();
      // this.year=this.myDate.getFullYear()//获取完整的年份
      
      // this.month  = this.myDate.getMonth()+1//获取当前月份
      // this.date   = this.myDate.getDate()//获取当前日
      // const days = this.myDate.getDay(); //获取当前星期X(0-6,0代表星期天) 
      
      // this.hours  = this.myDate.getHours(); //获取当前小时数(0-23) 
      // this.minutes = this.myDate.getMinutes(); //获取当前分钟数(0-59) 
      // this.seconds = this.myDate.getSeconds(); //获取当前秒数(0-59)  
      // const weeks = ["星期日","星期一","星期二","星期三","星期四","星期五","星期六"];
      // this.day = weeks[days]
      this.currentTime();
    },
    // 销毁定时器
    beforeDestroy: function() {
        if (this.getDate) {
            console.log("销毁定时器")
            clearInterval(this.getDate); // 在Vue实例销毁前，清除时间定时器
        }
    }
  }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
#box
   width 100%
   height 100%
   #box-header
    display flex
    justify-content space-between
    .header-right
     width 150px
     height 50px
     margin-right  20px
     display flex
     text-align center
     justify-content space-between
    //  background-image:url(../assets/1.png) 
    //  background-size 150px 50px
</style>
