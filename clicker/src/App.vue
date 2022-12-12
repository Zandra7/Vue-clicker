<script setup>
</script>

<template>
<div class="app">
  <h1 class="title">Cookie Clicker</h1>
  <h2>Cookies: {{count}}</h2>
  <h2>Cash: {{money}}$</h2>

  <img @click="click()" src="src/assets/cartoonCookie.png" alt="cookie to click">
  <br>
  <button @click="sell1()">Sell 1</button>
  <button @click="sell10()">Sell 10</button>
  <button @click="sell100()">Sell 100</button>
  <br>
  <button @click="sellall()">Sell all</button>
  <br>
  <br>
  <h3>Cost: {{cookieIncrease*20}}$</h3>
  <button @click="click2()">+1 Click</button>
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
      cookieIncrease: 1,
    }
  },
  methods: {
    click(){
      this.count += this.cookieIncrease
    },
    click2(){
      if (this.money >= this.cookieIncrease*20){
        console.log("hei")
        this.money -= this.cookieIncrease*20
        this.cookieIncrease++
      }
    },
    sell1(){
      if (this.count >= 0){
        this.money+=1
        this.count-=1
      }
    },
    sell10(){
      if(this.count > 9){
        this.money+=10
        this.count-=10
      }
    },
    sell100(){
      if(this.count > 99){
        this.money+=100
        this.count-=100
      }
    },
    sellall(){
      if(this.count > 0){
        this.money+=this.count
        this.count-=this.count
      }
    },
    buyAutocl(){
      if(this.money >= 150) {
        this.money -= 150
        this.check = setInterval(this.addCookies,1000);  
      }
    },
    sellAutocl(){
      if(this.check != null) {
        clearInterval(this.check)
        this.check = null
        this.money += 150

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

  img {
    height: 200px;  
  }
  button {
    font-size: 20px;
    padding:  10px 20px;
    margin-bottom: 1%;
    border: 1px solid rgb(0, 0, 0);
    border-radius: 5px;
    background: rgba(215, 153, 94, 0.969);
    cursor: pointer;
    width: 200px;
    height: 6%;
    color: rgb(65, 36, 10)
  }
</style>
