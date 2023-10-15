<template>
  <div class="main-container">
      <div class="center-container">
        <h1 class="header">А чого не на МОВІ??????</h1>
          <div class="question" v-for="(question, index) in questions" :key="index">
            <h3>{{ question.text }}</h3>

              <div class="question-column" v-if="question.type === 'text'">
                <label v-for="(option, oIndex) in question.options" :key="oIndex">
                  <input type="radio" :name="'q' + index" :value="oIndex" v-model="question.userAnswer" @change="verifyAnswer(question)">
                  <span :class="getOptionClass(question, oIndex)">{{ option.text }}</span>
                </label>
              </div>

              <div v-else-if="question.type === 'image'">
                  <!-- Replace with your image components or paths -->
                  <!-- For simplicity, we are using placeholder images here -->
                  <img v-for="(option, oIndex) in question.options" 
                    :key="oIndex" class="img" 
                    :src="getImgUrl(option.image)" 
                    @click="selectImageAnswer(index, oIndex)"
                    :class="['img', getOptionClass(question, oIndex), { 'selected-image': question.userAnswer === oIndex }]"     
                    >
              </div>
          </div>
          <button 
            class="glow-on-hover second-class" 
            v-if="(!isAllAnswersCorrect) || (isAllAnswersCorrect && !isWasTry)"
            @click="checkCode">
            Давай перевіримо тебе
          </button>
          <button 
            class="glow-on-hover second-class" 
            v-if="isWasTry && isAllAnswersCorrect"
            @click="$emit('nextStep')">
            Добре москалику, ходімо далі
          </button>
      </div>
  </div>
</template>

<script>
export default {
  name: 'MovaComponent',
  data() {
    return {
      isWasTry: false,
      questions: [
        {
          type: 'text',
          text: 'В якому рядку всі слова потрібно писати без апострофа?',
          options: [
            { text: 'дит..ясла, Дансм..юр, ад..ютант, Гур..єв;' },
            { text: 'верб..я, між..ярусний, тьм..яний, без..ядерний;' },
            { text: 'дзв..якнути, моркв..яний, медв..яний, різдв..яний.', correct: true }
          ],
          userAnswer: null,
          answered: false 
        },
        {
          type: 'image',
          text: 'Що з цього “ночви”?',
          options: [
            { image: 'test1' },
            { image: 'test2' },
            { image: 'test3', correct: true  },
            { image: 'test4' }
          ],
          userAnswer: null,
          answered: false 
        },
        {
          type: 'text',
          text: 'Що означає фразеологізм “шашиль точити”?',
          options: [
            { text: 'жогло на пікніку' },
            { text: 'їсти шашличок' },
            { text: 'переживати', correct: true },
            { text: 'посягати на щось' }
          ],
          userAnswer: null,
          
        }
      ]
    };
  },
  computed: {
    isAllAnswersCorrect() {
      return this.questions.every(q => q.userAnswer !== null && q.options[q.userAnswer]?.correct);
    }
  },
  methods: {
    checkCode(){
      this.isWasTry = true;
    },
    selectImageAnswer(questionIndex, optionIndex) {
      this.isWasTry = false;
      this.questions[questionIndex].userAnswer = optionIndex;
    },
    getOptionClass(question, optionIndex) {
      if (question.userAnswer === null) return '';

      if (question.userAnswer === optionIndex && this.isWasTry) {
          return question.options[optionIndex].correct ? 'correct-answer' : 'wrong-answer';
      }
      return '';
    },
    verifyAnswer(question) {
      this.isWasTry = false;
      question.answered = true;
    },
    getImgUrl(pet) {
      let images = require.context('../assets/', false, /\.png$/)
      return images('./' + pet + ".png")
    }
  }
}
</script>
<style lang="scss" scoped>

$primary-color: #00005c;
    .main-container {
      background-image: url("../assets/movaFone.png");
      background-position-y: -60px;
      max-height: 100vh;
      overflow-y: scroll;
    }
    .center-container{
        justify-content: start;
        text-align: left;
        max-width: 100%;
        height: 100%;
        padding-bottom: 20px;
    }
    .img{
      width: 250px;
      height: 250px;
      margin: 0 10px;
      border-radius: 15px;
      border: 4px solid transparent;
    }
    .header {
        color: yellow;
        position: relative;
        margin: 10px 0;
    }
  
    .second-class {
        margin: 0 25px;
        background-color: blue;
        color: yellow;
    }

    .selected-image {
      border: 4px solid black;  /* You may adjust the color and width as per your design */
      box-shadow: 0px 0px 10px 5px rgba(0,0,0,0.5);  /* Optional: for additional emphasis */
      cursor: pointer;  /* Indicates that the image is clickable */
    }
   
    .correct-answer {
    color: green;
}

.wrong-answer {
    color: red;
}

/* For the image options */
.img.correct-answer {
    border: 4px solid green;
}

.img.wrong-answer {
    border: 4px solid red;
}
.question {
  font-size: 25px;
  width: 80%;
  margin: 0 auto;
}
.question-column{
  display: flex;
  flex-direction: column;
  width: 100%;
}

label {
  display: flex;
  cursor: pointer;
  font-weight: 500;
  position: relative;
  overflow: hidden;
  margin-bottom: 0.375em;
  /* Accessible outline */
  /* Remove comment to use */ 
  /*
    &:focus-within {
        outline: .125em solid $primary-color;
    }
  */
  input {
    position: absolute;
    left: -9999px;
    &:checked + span {
      background-color: mix(#fff, $primary-color, 84%);
      &:before {
        box-shadow: inset 0 0 0 0.4375em $primary-color;
      }
    }
  }
  span {
    display: flex;
    align-items: center;
    padding: 0.375em 0.75em 0.375em 0.375em;
    border-radius: 99em; // or something higher...
    transition: 0.25s ease;
    &:hover {
      background-color: mix(#fff, $primary-color, 84%);
    }
    &:before {
      display: flex;
      flex-shrink: 0;
      content: "";
      background-color: #fff;
      width: 1.5em;
      height: 1.5em;
      border-radius: 50%;
      margin-right: 0.375em;
      transition: 0.25s ease;
      box-shadow: inset 0 0 0 0.125em $primary-color;
    }
  }
}

  </style>