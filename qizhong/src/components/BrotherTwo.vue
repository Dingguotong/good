<template>
  <div class="two">
      <div class="gt_left">
          <div>
          <h3>正在进行</h3>
          <!-- 计数 -->
              <span>{{gtjx}}</span>
          <!-- 循环渲染，并且判断是否显示 -->
          <p v-for='(a,i) in msg' v-if='!a.check'>
              <!-- 复选框 -->
              <input type="checkbox" @click='bian(i)' :checked='a.check'>
              {{a.name}}
              <span @click='del(i)'>X</span>
          </p>
      </div>
      <div>
          <h3>已完成</h3>
          <!-- 计数 -->
           <span>{{gtwc}}</span>
          <!-- 循环渲染，并且判断是否显示 -->
          <p v-for='(a,i) in msg' v-if='a.check'>
              <!-- 复选框 -->
              <input type="checkbox" @click='bian(i)' :checked='a.check'>
              {{a.name}}
              <span @click='del(i)'>X</span>
          </p>
      </div>
      </div>
      <!-- 全部 -->
      <div class="gt_right">
         
          <h3>全部</h3>
          <!-- 计数 -->
           <span>{{gtzs}}</span>
           <!-- 循环渲染 -->
          <p v-for='(a,i) in msg'>
                <!-- 复选框 -->
              <input type="checkbox" @click='bian(i)' :checked='a.check'>
              {{a.name}}
              <span @click='del(i)'>X</span>
          </p>
      </div>
  </div>
</template>

<script>
// 引入bus
import bus from './bus'
export default {
  name: 'BrotherTwo',
  data() { 
    return {
        msg:[]
    }
  },
  props: [

  ],
   computed:{
            gtzs(){
                return this.msg.length
            },
            gtjx(){
                var jx=this.msg.filter((v)=>{
                    return v.check
                })
                return this.msg.length-jx.length
            },
            gtwc(){
                var jx=this.msg.filter((v)=>{
                    return v.check
                })
                return this.msg.length-!jx.length
            }
   },
  components:{
  },
  mounted() {
      this.gt_ad()
  },
  methods:{
      gt_ad(){
        //   改变this指向
          let that=this
        //   接收兄弟组件传过来的值
          bus.$on('ad',function(val){
              that.msg=val
          })
      },
    //   、点击改变复选框当前属性
      bian(n){
          this.msg[n].check=!this.msg[n].check
      },
    //   删除功能
      del(n){
          this.msg.splice(n,1)
      }
  },
 }
</script>

<style lang="scss" scoped>
.two{
    width: 100%;
    display: flex;
    .gt_left{
        width: 50%;
    }
}
</style>