<script setup>
</script>

<template>
<div class="app">
  <h1 class="title">{{title}}</h1>
  <h2>Cookies: {{count}}</h2>
  <h2>Cash: {{money}}$</h2>

  <button @click="count++">Buy cookies</button>
  <br>
  <button @click="count--">Sell 1</button>
  <button @click="(money+=10, count-=10)">Sell 10</button>
  <button @click="(money+=100, count-=100)">Sell 100</button>
  <br>
  <button @click="(money+=count, count=0)">Sell all</button>

</div>
</template>


<style scoped>
  .app {
    text-align: center;
  }
  .title {
  margin-top: 2%;
}

  button {
    font-size: 20px;
    padding:  10px 20px;
    margin-bottom: 1%;
    border: 1px solid #ccc;
    border-radius: 5px;
    background: #fff;
    cursor: pointer;
  }



</style>


<script>
export default {
  data: function(){
    return {
      title: 'Clicker Website',
      count: 0,  
      money: 0,

    }
  }
}
</script>
