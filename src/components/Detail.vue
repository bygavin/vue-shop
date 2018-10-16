<template>
  <div>
    yes  i am content
  </div>
</template>
<script>
  export default{

      data(){
        return {
          num:10
        }
      },
      mounted(){
          console.log('init');
      },
      created:function(){
        let id = this.$route.query.id; //获取get请求参数的方式
        console.log('商品id:');
        console.log(id);
      },
      methods:{

      }
  }

</script>
