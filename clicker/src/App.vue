<script setup>
</script>

<template>
<div class="app">
  <h1 class="title">Cookie Clicker</h1>
  <h2>Cookies: {{count}}</h2>
  <h2>Cash: {{money}}$</h2>

  <button @click="click()">Get cookies</button>
  <br>
  <button @click="sell1()">Sell 1</button>
  <button @click="sell10()">Sell 10</button>
  <button @click="sell100()">Sell 100</button>
  <br>
  <button @click="sellall()">Sell all</button>
  <br>
  <br>
  <h3>Cost: 150$</h3>
  <button @click="buyAutocl()">Buy autoclicker</button>
  <button @click="sellAutocl()" v-if="(check!=null)">Sell autoclicker</button>


</div>
</template>

<script>

export default {
  data(){
    return {
      count: 0,
      money: 0,
      check: null,

    }
  },
  methods: {
    click(){
      this.count++
    },
    sell1(){
      if (this.count > 0){
        console.log("1")
        this.money+=1*2
        this.count-=1
      }
    },
    sell10(){
      if(this.count > 9){
        this.money+=10*2
        this.count-=10
      }
    },
    sell100(){
      if(this.count > 99){
        this.money+=100*2
        this.count-=100
      }
    },
    sellall(){
      if(this.count > 0){
        this.money+=this.count*2
        this.count-=this.count
      }
    },
    buyAutocl(){
      if(this.money > 1) {
        this.money -= 150
        this.check = setInterval(this.addCookies,1000);  
      }
    },
    sellAutocl(){
      if(this.check != null) {
        clearInterval(this.check)
        this.check = null
        
      }
    },
    addCookies(){
      this.count += 1
    },
}
}
</script>

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
    width: 200px;
    height: 6%;
  }
</style>
