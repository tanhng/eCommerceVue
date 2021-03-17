<template>
<div >
    <div class="row">
        <div v-for="item in data" :key="item.id" class="card" style="width: 18rem;">
            <img class="card-img-top" :src="require(`../assets/${item.imageURL}`)" alt="Card image cap">
            <div class="card-body">
        <h5 class="card-title">{{item.title}}</h5>
        <p class="card-text">{{item.description}}</p>
        <a href="#" class="btn btn-primary">Add to cart</a>
            </div>
        </div>
    </div>
</div>
</template>

<script>

export default {

  name: 'Content',
  props:['data'],
  components: {

  }
}
</script>

<style>
.card{
    margin:20px;
    padding:auto;
}

.row{
    margin:auto;
    padding:auto;
}
</style>
