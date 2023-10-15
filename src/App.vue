<template>
  <div>
    <template v-if="currentStep == 0">
       <WelcomeComponent @nextStep="nextStep"></WelcomeComponent>
    </template>
    <template v-if="currentStep == 1">
      <SecondComponent @nextStep="nextStep"></SecondComponent>
    </template>
    <template v-if="currentStep == 2">
      <ThirdComponent @nextStep="nextStep"></ThirdComponent>
    </template>
    <template v-if="currentStep == 3">
      <MovaComponent @nextStep="nextStep"></MovaComponent>
    </template>
    <template v-if="currentStep == 4">
      <TehnichkaComponent @nextStep="nextStep"></TehnichkaComponent>
    </template>
    <template v-if="currentStep == 5">
      <LastComponent @nextStep="nextStep"></LastComponent>
    </template>
    <template v-if="currentStep == 6">
      <RealLastComponent @nextStep="nextStep"></RealLastComponent>
    </template>
  </div>
</template>

<script>
import WelcomeComponent from './components/WelcomeComponent.vue'
import SecondComponent from './components/SecondComponent.vue'
import ThirdComponent from './components/ThirdComponent.vue'
import MovaComponent from './components/MovaComponent.vue'
import TehnichkaComponent from './components/TehnichkaComponent.vue'
import LastComponent from './components/LastComponent.vue'
import RealLastComponent from './components/RealLastComponent.vue'

export default {
  name: 'App',
  components: {
    WelcomeComponent,
    SecondComponent,
    ThirdComponent,
    MovaComponent,
    TehnichkaComponent,
    LastComponent,
    RealLastComponent,
},
  data() {
    return {
      currentStep: 0,
    }
  },
  methods: {
    nextStep() {
      this.currentStep++;
    }
  }

  
}
</script>

<style>
body{
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100%;
  height: 100%;
}
.main-container {
  width: 100vw;
  height: 100vh;
  background-size: cover;
  background-repeat: no-repeat;
}
.center-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 80vh;
}


.glow-on-hover {
    font-size: 20px;
    width: 220px;
    height: 50px;
    border: none;
    outline: none;
    color: #fff;
    background: transparent;
    cursor: pointer;
    position: relative;
    z-index: 0;
    border-radius: 10px;
}

.glow-on-hover:before {
    content: '';
    background: linear-gradient(45deg, #ff0000, #ff7300, #fffb00, #48ff00, #00ffd5, #002bff, #7a00ff, #ff00c8, #ff0000);
    position: absolute;
    top: -2px;
    left:-2px;
    background-size: 400%;
    z-index: -1;
    filter: blur(5px);
    width: calc(100% + 4px);
    height: calc(100% + 4px);
    animation: glowing 20s linear infinite;
    opacity: 0;
    transition: opacity .3s ease-in-out;
    border-radius: 10px;
}

.glow-on-hover:active {
    color: #000
}

.glow-on-hover:active:after {
    background: transparent;
}

.glow-on-hover:hover:before {
    opacity: 1;
}

.glow-on-hover:after {
    z-index: -1;
    content: '';
    position: absolute;
    width: 100%;
    height: 100%;
    background: transparent;
    left: 0;
    top: 0;
    border-radius: 10px;
}

@keyframes glowing {
    0% { background-position: 0 0; }
    50% { background-position: 400% 0; }
    100% { background-position: 0 0; }
}
</style>
