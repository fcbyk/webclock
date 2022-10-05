<template>
  <div>
    <p>距离 2022下半年 CET-4</p>
    <h1>{{day}} 天 {{hour}} 小时 {{min}} 分钟 {{sec}} 秒</h1>
  </div>
</template>

<script>  
  export default {
    name:'App',
    data() {
      return {
        now:'',
        CET4:'',
        sec:'',
        min:'',
        hour:'',
        day:'',
        interval:'',
        timer:''
      }
    },
    mounted() {
      this.CET4 = new Date("2022/12/10 9:00").getTime()
      this.timer = setInterval(()=>{
        if(this.interval>=0){
        this.now = new Date().getTime()
          this.interval = (this.CET4-this.now)/1000
          this.day = Math.floor(this.interval/(60*60*24))
          this.hour = Math.floor(this.interval/(60*60)%24).toString().padStart(2,'0')
          this.min = Math.floor(this.interval/60%60).toString().padStart(2,'0')
          this.sec = Math.floor(this.interval%60).toString().padStart(2,'0')
        }else{
          clearInterval(this.timer)
          this.day = 0
          this.hour = 0
          this.min = 0
          this.sec = 0
        }
      },1000)
    },
  }
</script>

<style>
*{
  padding: 0;
  margin: 0;
}
body{
  background: #2d3436;
  height: 100vh;
  width: 100vw;
  box-sizing: border-box;
  display: flex;
  justify-content: center;
  align-items: center;
}
div{
  color: #dfe6e9;
  /* font-size: 20px ; */
  font-family: SanFrancisco;
}
p{
  font-size: 1.2em;
  margin-bottom: 10px;
  text-align: center;
  font-style: italic;
  color: #b2bec3;
}
h1{
  font-size: 1.7em;
}
</style>
