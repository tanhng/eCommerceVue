<template>
  <div id="app">
    <FilterNav :productType='productType' @productTypeWasUpdated="productTypeUpdate"  />
    <Content :productType='productType'  :data='data' />
    <Pagination/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import FilterNav from './components/FilterNav'
import database from './database/products.json'
import Content from './components/Content'
import Pagination from './components/Pagination'
export default {
  name: 'App',
  data(){
    return{
      data: database.products,
      productType: "default",
    }
  },
  components: {
    FilterNav,
    Content,
    Pagination,
  },
  methods:{
    productTypeUpdate:function(value){
      if(value=="default"){
        this.data=database.products;
        return;
      }
      this.productType=value;
      console.log(this.productType);
      this.data=database.products.filter((item)=>{return item.type==value;})
      console.log(this.data);
    }
  },
}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
