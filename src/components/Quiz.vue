<template>
  <div class="flex flex-col gap-8 ">
    <h1 class="text-2xl">{{ leftOperand }} {{ operators }} {{ rightOperand }}</h1>
    <div class="flex gap-5 ">
      <button @click="selectedAnswer" v-for="(answer, index) of answers" :key="index"
        class="bg-[#417079] w-full p-3 h-[80px] text-white align-top rounded text-2xl leading-6 capitalize">{{ answer
        }}</button>
    </div>
    <div class="flex items-center justify-center gap-6 w-full">
      <button @click="startQuiz" v-if="!isStarted"
        class="bg-[#1a434d] w-full p-3 h-[80px] text-white align-top rounded text-2xl leading-6 capitalize">Start</button>
      <button @click="$emit('back')"
        class="bg-[#1a434d] w-full p-3 h-[80px] text-white align-top rounded text-2xl leading-6 capitalize">Back</button>
      <!-- <button @click="startQuiz" v-if="isStarted" class="bg-[#1a434d] w-full p-3 h-[80px] text-white align-top rounded text-2xl leading-6 capitalize">next</button> -->
    </div>
  </div>
</template>

<script>
export default {
  name: 'Quiz',

  props: [
    "operators",
  ],
  data() {
    return {
      leftOperand: null,
      rightOperand: null,
      isStarted: false,
      answers: [],
      correctAnswer: '',
      lastanswer: '',
      error: false,
    }
  },
  methods: {
    selectedAnswer(event) {
      if (event) {
        let answer = Number(event?.target.innerText)
        if (answer !== this.correctAnswer) {
          // alert("please select a correct answer");
          event.target.classList.add("incorrect");
          setTimeout(() => {
            this.answers = [];
            this.startQuiz();
            event.target.classList.remove("incorrect");
          }, 700);
          // console.log(event.target.classList.contains('incorrect'));
        } else {
          event.target.classList.add("correct");
          setTimeout(() => {

            this.answers = [];
            this.startQuiz();
            event.target.classList.remove("correct");
          }, 700);
          // console.log(event.target.classList.contains('correct '));
        }

      }
    },
    startQuiz() {

      this.isStarted = true
      this.leftOperand = parseInt(Math.random() * 13)
      this.rightOperand = parseInt(Math.random() * 13)

      const methods = {
        "+": (a, b) => a + b,
        "-": (a, b) => a - b,
        "*": (a, b) => a * b,
        "/": (a, b) => a / b,
      }

      const methodToUse = methods[this.operators]
      // console.log(methodToUse)

      for (let i = 0; i < 4; i++) {
        const answer = methodToUse(this.leftOperand *  this.randomIntFromInterval(1, 3), this.rightOperand * this.randomIntFromInterval(1, 3));
        // console.log(answer)
        this.answers.push(answer);
        // console.log(this.answers)
      }


      // correct answer
      this.correctAnswer = eval(`${this.leftOperand}${this.operators}${this.rightOperand}`)
      this.answers[parseInt(Math.random() * this.answers.length)] = this.correctAnswer
      console.log(this.correctAnswer)

      // correct answer
      // const expectedAnswer = methodToUse(this.leftOperand, this.rightOperand);
      // this.answers[parseInt(Math.random() * this.answers.length)] = expectedAnswer
      // console.log(this.answers)
    },

    randomIntFromInterval(min, max) { // min and max included 
      return Math.floor(Math.random() * (max - min + 1) + min)
    }
  },

}
</script>

<style scoped>
.correct {
  background-color: #41b613 !important;
}

.incorrect {
  background-color: #ed4337 !important;
}
</style>
