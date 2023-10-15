<template>
    <div class="main-container">
        <div class="center-container">
            <h1 class="header">
            Hello, Nikitosik
            </h1>
            <div class="greetings">
                We welcome you to the magical world! 
            </div>
            <img src="../assets/we.png" alt="Nikita's BEST friends">
        </div>
        <button class="glow-on-hover" @click="this.$emit('nextStep');">
            Let's go to magic!
        </button>
    </div>
</template>

<script>
export default {
  name: 'WelcomeComponent',
}
</script>

<style scoped>
.main-container {
  background-image: url("../assets/fone.jpg");
}
.glow-on-hover {
  background-color: green;
}
.header {
  font-size: 35px;
  color: #131212;
  opacity: 0.8;
  text-shadow:
    0 0 7px #fff,
    0 0 10px #fff,
    0 0 21px #fff,
    0 0 42px rgb(10, 131, 91),
    0 0 82px rgb(10, 131, 91),
    0 0 92px  rgb(10, 131, 91),
    0 0 102px rgb(10, 131, 91),
    0 0 151px rgb(10, 131, 91);
}
.greetings {
    width: 100%;
  margin-top: 20px;
   text-transform: uppercase;
  background-image: linear-gradient(
    -225deg,
    #231557 0%,
    #44107a 29%,
    #ff1361 67%,
    #fff800 100%
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
      font-size: 25px;
}

@keyframes textclip {
  to {
    background-position: 200% center;
  }
}
</style>
