<template>
    <div class="main-container">
        <div class="center-container">
            <h1 class="header" > 
                {{ headerText }}
            </h1>
            <div class="btn-row" v-if="!happy">
                <button class="glow-on-hover second-class" @click="congrats"> Переплыть через реку </button>
                <button class="glow-on-hover second-class" @click="thinkMore"> Погулять в лесу </button>
            </div>
            <div v-else>
                <h2 class="wish">
                    Магический мир в Европе для тебя пусть будет открыт
                </h2>
                <img class="img" src="../assets/HB.png" alt="Nikita's BEST friends">
                <div class="gift">
                    Иди искать подарки, Огурец!
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
  name: 'RealLastComponent',
  data() {
    return {
        headerText: "Ладно, никакого Бахмута. Что тебе нужно для счастья?", 
        happy: false, 
      };
  },
  methods: {
    thinkMore () {
        alert("Подумай еще")
    },
    congrats() {
        this.headerText = "Поздравляем с Днем Рождения!!!"
        this.happy = true
    }
  },
  
}

</script>
<style scoped>
.main-container{ 
    background-image: url("../assets/gift.png");
    background-size: contain;
    background-position: center;
}
.second-class {
    background-color: blueviolet;
}
.btn-row{
    display: flex;
    flex-direction: row;
    gap: 30px;
}
.img{
    height: 500px;
}
.header {
    text-align: center;
    width: 100%;
    margin-top: 20px;
     text-transform: uppercase;
    background-image: linear-gradient(
      -225deg,
      #27df0f 0%,
      #161615 29%,
      #ff1361 67%,
      #15ddd3 100%
    );
    background-size: auto auto;
    background-clip: border-box;
    background-size: 200% auto;
    color: #fff;
    background-clip: text;
    text-fill-color: transparent;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    animation: textclip 2s linear infinite;
    display: inline-block;
    font-size: 35px;
}
@keyframes textclip {
  to {
    background-position: 200% center;
  }
}
.wish{
    font-size: 25px;
    text-shadow: 2px 2px 5px red;
    color: beige;
}
.gift {
    font-size: 25px;
    text-shadow: 2px 2px 5px red;
    padding-left: 2px;

}
</style>