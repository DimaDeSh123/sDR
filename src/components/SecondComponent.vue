<template>
    <div class="main-container">
        <div class="center-container">
            <h1 class="header">Упс, вместо "magic world" ты попал в матрицу</h1>
            <p class="riddle">{{ riddle }}</p>
            <input class="input" type="text" v-model="enteredCode">
            <button class="glow-on-hover second-class" @click="checkCode">Проверить</button>
            <transition name="fade">
                <p class="wrong-answer" v-if="message">{{ message }}</p>
            </transition>
        </div>
       
    </div>
</template>
<script>
export default {
  name: 'SecondComponent',
  data() {
    return {
      riddle: "Отгадай код. Попробуй добавить день, месяц, год и время, чтобы выбраться отсюда", 
      enteredCode: "",
      correctCode: "4911", 
      message: "",
    };
  },
  methods: {
    checkCode() {
      if (this.enteredCode === this.correctCode) {
        this.$emit('nextStep');
      } else {
        this.message = "Матрица беспощадна. Ты все еще тут";
      }
    },
  },
}
</script>
<style scoped>
.main-container {
  background-image: url("../assets/secondFone.jpg");
}
.header {
    color: #04fa18;
    position: relative;
    margin: 0;
    margin-bottom: 10px;
    top: -15px;
}
.riddle{
    position: relative;
    margin: 0;
    top: -15px;
    font-size: 30px;
    max-width: 700px;
    color: white;
    text-shadow: rgb(51, 243, 3) 5px 5px 10px;
}
.input {
  margin-top: 2rem;
  box-sizing: border-box;
  background-color: #fff;
  padding: 0.7rem;
  border: none;
  font-size: 1rem;
  color: hsla(260, 2%, 25%, 0.7);
  width: 300px;
  margin-bottom: 20px;
  box-shadow: 0 0 5px #fff, 0 0 10px #fff, 0 0 20px #0ff, 0 0 30px #0ff,
    0 0 40px rgb(2, 247, 55);
}
.second-class {
    margin-top: 15px;
    background-color: green;
}
.wrong-answer{
    color: red;
    text-shadow: rgb(1, 3, 0) 5px 5px 10px; ;
    position: absolute;
    font-weight: 600;
    font-size: 38px;
    top: 57%;

}

.fade-enter-active, .fade-leave-active {
  transition: opacity 2.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
  opacity: 0;
}

 </style>


