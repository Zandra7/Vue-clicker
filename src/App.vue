<template>
<div class="app">
  <h1 class="title">Cookie Clicker</h1>
  <h2>Cookies: {{count}}</h2>
  <h2>Cash: {{money}}$</h2>

  <img @click="click()" src="src/assets/cartoonCookie.png" alt="cookie to click">
  <br>
  <button @click="sell1()">Sell 1</button>
  <button @click="sellall()">Sell all</button>
  <br>
  <br>
  <h3>Cost: {{cookieIncrease*20}}$</h3>
  <button @click="click2()">+1 Click</button>
  <br>
  <h3>{{autoclPrice}}$</h3>
  <button v-if="!hasAutoclicker" @click="buyAutocl()">Buy autoclicker</button>
  <button v-else @click="addClickToAutocl()">Add click to autoclicker</button>


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
      hasAutoclicker: false,
      autoClickerIncrease: 1,
      autoclPrice: 150,
    }
  },
  methods: {
    click(){
      this.count += this.cookieIncrease
    },
    click2(){
      if (this.money >= this.cookieIncrease*20){
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
    sellall(){
      if(this.count > 0){
        this.money+=this.count
        this.count-=this.count
      }
    },
    buyAutocl(){
      if(this.money >= 150) {
        console.log(this.autoclPrice)
        this.money -= 150
        this.hasAutoclicker = true
        this.check = setInterval(this.addCookies.bind(this), 1000)
        this.autoclPrice *= 2
        console.log(this.autoclPrice)
      }
    },
    addClickToAutocl(){
      if(this.money >= this.autoclPrice){
        this.autoClickerIncrease += 1
        this.autoclPrice *= 2
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
      this.count += this.autoClickerIncrease
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
