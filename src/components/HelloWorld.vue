<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>

    <h2>Ecosystem</h2>
    <ul>
      <li v-for="item in itemList">{{ item.goodsName}} / {{ item.marketPrice}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      itemList:[]
    }
  },
  mounted(){
     console.log('start');
     this.initData();
     this.getCategory();
  },
  methods:{
     initData:function(){
        this.$http.get('/category/goods').then(res => {
            console.log(res.data.data);
        }).catch( err => {

        })
     },
     getCategory:function(){
       this.$http.get('/category/goods').then(res =>{
          let list = res.data.data.goodsList;
          list.forEach((item,index) => {
              console.log(index);
              var item = {goodsName:item.goodsName,marketPrice:item.marketPrice};
              this.itemList.push(item);
           })
       }).catch(err =>{

       })
     },

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
