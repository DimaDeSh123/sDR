<template>
    <div class="main-container">
        <h1 class="header">Ты вернулся в реальный мир, но он жесток. Чтобы выжить, нужны шутки про говно и не только</h1>

        <div class="center-container">
            <div class="riddle-row">
                <p class="riddle">{{ riddle }}</p>
                <input class="input" type="text" v-model="firstAnswer">
            </div>
            <div class="riddle-row">
                <p class="riddle">{{ secondRiddle }}</p>
                <input class="input" type="text" v-model="secondAnswer">
            </div>
            <div class="riddle-row">
                <p class="riddle">{{ thirdRiddle }}</p>
                <input class="input" type="text" v-model="thirdAnswer">
            </div>
           
            <button class="glow-on-hover second-class" @click="checkCode" :disabled="firstAnswer && secondAnswer && thirdAnswer">Проверить</button>
        </div>
       
    </div>
</template>
<script>
export default {
  name: 'ThirdComponent',
  data() {
    return {
      riddle: "Лучший подарок под елкой", 
      secondRiddle: "Если друзья закрыли дверь", 
      thirdRiddle: "Чем кормить Тоби", 
      secondAnswer: "",
      firstAnswer: " ", 
      thirdAnswer: "",
      };
  },
  methods: {
    checkCode() {
        this.$emit('nextStep');
    },
  },
}
</script>
<style scoped>
    .main-container {
      background-image: url("../assets/thirdfone.png");
    }
    .center-container{
        justify-content: start;
        margin-top: 150px;
    }
    .header {
        color: #694002;
        position: relative;
        margin: 0;
        margin-bottom: 10px;
    }
    .riddle-row{
        display:flex; 
        flex-direction: row;
        align-items: baseline;
        justify-content: space-between;
        margin: 0 auto;  
        width: 80%;

    }
    .riddle{
        margin: 0;
        font-size: 40px;
        max-width: 700px;
        color: rgb(15, 0, 0);
        text-shadow: rgb(249, 252, 249) 5px 5px 10px;
        background-color: rgba(233, 188, 117, 0.36);
        
    }
    
    
    .input {
      margin-top: 2rem;
      margin-right: 100px;
      box-sizing: border-box;
      background-color: #fff;
      padding: 0.7rem;
      border: none;
      font-size: 1rem;
      color: hsla(260, 2%, 25%, 0.7);
      width: 300px;
      margin-bottom: 20px;
      box-shadow: 0 0 5px #fff, 0 0 10px #fff, 0 0 20px #694002, 0 0 30px #694002,
        0 0 40px #694002;
    }
   

    .second-class {
        margin-top: 15px;
        background-color: #694002;
    }
</style>
    
    
    