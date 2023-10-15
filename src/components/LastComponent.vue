<template>
    <div class="main-container">
        <div class="center-container">
            <h1 class="header" :class="{'margin-top': !isTenSecondsPast}"> 
                {{ headerText }}
            </h1>
            <div v-if="isTenSecondsPast">
                <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d21106.01625802152!2d37.98217953494226!3d48.605018793836145!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x40dfe61bf724c5a7%3A0xa398e255ecbfeec2!2z0JHQsNGF0LzRg9GCLCDQlNC-0L3QtdGG0YzQutCwINC-0LHQu9Cw0YHRgtGM!5e0!3m2!1suk!2sua!4v1697386992120!5m2!1suk!2sua" width="900" height="550" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
            </div>
        </div>
       
        <button v-if="isTenSecondsPast" class="btn" @click="this.$emit('nextStep');">
            Прийняти оффер
        </button>
        <button v-if="isTenSecondsPast" class="btn" @click="this.$emit('nextStep');" disabled>
            Відмовитись
        </button>
    </div>
</template>

<script>
export default {
  name: 'LastComponent',
  data() {
    return {
      headerText: "А тепер як справжній програміст встанови ВІНДУ!", 
      isTenSecondsPast: false, 

      };
  },
  methods: {
    checkCode() {
        this.$emit('nextStep');
    },
  },
  mounted() {
    setTimeout(() => {
        this.isTenSecondsPast = true;
        this.headerText = "Гаразд, пожартували й досить. Для тебе є СУПЕР вакансія"
    }, "10000");
  }
}

</script>

<style scoped>
    .main-container {
      background-image: url("../assets/window-2005298_1280.png");
      background-size: contain;
      background-repeat: no-repeat;
      background-position: center;
    }
    .header {
        font-size: 45px;
        color: rgb(24 29 255);
    }
    .margin-top {
        margin-bottom: 200px;
    }
    .btn {
        padding: 10px 15px;
        font-size: 25px;
        margin-left: 10px;
        color: black;
        background-color:rgb(24 29 255);
    }
    .btn:disabled {
        opacity: 0.5;
    }
</style>