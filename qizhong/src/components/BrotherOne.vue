<template>
  <div class="gt_One">
      <input type="text" v-model='text' @keyup.enter='add'>
  </div>
</template>

<script>
// 引入bus
import bus from './bus'
export default {
  name: 'BrotherOne',
  data() { 
    return {
        text:'',
        obj:{},
        arr:[

        ]
    }
  },
  props: [

  ],
  components:{
  },
  mounted() {

  },
  methods:{
    //   数据添加
      add(){
          this.obj={name:this.text,check:false}
          this.arr.push(this.obj)
          console.log(this.arr)
        //   兄弟组件传值
          bus.$emit('ad',this.arr)
      }
  },
 }
</script>

<style lang="scss" scoped>
.gt_One{
    input{
        width: 100%;
        height: 30px;
    }
}
</style>