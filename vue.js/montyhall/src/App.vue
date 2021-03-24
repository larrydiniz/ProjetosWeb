<template>
  <div id="app">
    <h1>É a porta dos desesperados!</h1>
    <div class="form">
      <div v-if="!started">
        <label for="portsAmount">Quantas portas deseja?</label>
        <input type="text" id="portsAmount" v-model.number="portsAmount">
      </div>
      <div v-if="!started">
        <label for="selectedPort">Qual é a porta premiada?</label>
        <input type="text" id="selectedPort" v-model.number="selectedPort">
      </div>
      <button v-if="!started" @click="started = true">Iniciar</button>
      <button v-if="started" @click="started = false">Reiniciar</button>
    </div>
    <div class="doors" v-if="started">
      <div v-for="i in portsAmount" :key="i">
          <Door :hasGift="i === selectedPort" :number="i" />
      </div>
    </div>
  </div>
</template>

<script>
import Door from './components/Door.vue'

export default {
  name: 'App',
  components: {
    Door
  },
  data: function(){
    return {
      started: false,
      portsAmount: 3,
      selectedPort: null
    }
  }
}
</script>

<style>
* {
    box-sizing: border-box;
    font-family: 'Montserrat', sans-serif;
}
body {
    color: #FFF;
    background: linear-gradient(to right, rgb(79, 182, 130), rgb(64, 124, 185));
}
#app {
    display: flex;
    flex-direction: column;
    align-items: center;
}
#app h1 {
    background-color: #0004;
    border-radius: 33px;
    padding: 20px;
    margin-bottom: 60px;
}
.form {
    max-width: 600px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 40px;
}

.form{
    margin-bottom: 10px;
    font-size: 2rem;
}

.form div{
  align-self: flex-start;
}

.form input{
  color: white;
  font-size: 1.5rem;
  margin-left: 20px;
  border: 1px solid rgba(255, 255, 255, 0.555);
  border-radius: 8px;
  background: transparent;
  padding: 0 10px;
  width: 50px;
}

.form button{
  font-size: 1.5rem;
  margin-top: 20px;
  padding: 10px;
  color: white;
  font-weight: 600;
  background: rgba(255, 255, 255, 0.151);
  border-radius: 15px;
  border: transparent;
}

.doors {
    align-self: stretch;
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
}
</style>
