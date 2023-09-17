<template>
  <div class="flex flex-col gap-8 ">
    <h1 class="text-2xl">{{ leftOperand }} {{operators}} {{ rightOperand }}</h1>
    <div class="flex gap-5">
      <button v-for="answer of answers" :key="answer" class="bg-[#1a434d] w-full p-3 h-[80px] text-white align-top rounded text-2xl leading-6 capitalize">{{ answer }}</button>
      <button v-if="isStarted" class="bg-[#1a434d] w-full p-3 h-[80px] text-white align-top rounded text-2xl leading-6 capitalize">{{ lastanswer }}</button>
    </div>
    <div class="flex items-center justify-center gap-6 w-full">
      <button @click="startQuiz" v-if="!isStarted"
        class="bg-[#1a434d] w-full p-3 h-[80px] text-white align-top rounded text-2xl leading-6 capitalize">Start</button>
      <button @click="$emit('back')" class="bg-[#1a434d] w-full p-3 h-[80px] text-white align-top rounded text-2xl leading-6 capitalize">Back</button>
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
      lastanswer: ''
    }
  },
  methods: {
    startQuiz() {
      this.isStarted = true
      this.leftOperand = parseInt(Math.random() * 13)
      this.rightOperand = parseInt(Math.random() * 13)
      for (let i = 0; i < 3; i++) {
        const answer = this.leftOperand * parseInt(Math.random()*3) + this.rightOperand * parseInt(Math.random() * 3)
        // console.log(answer)
        this.answers.push(answer);
      }
      this.correctAnswer = (`${this.leftOperand}${this.operators}${this.rightOperand}`)
      this.lastanswer = eval(this.correctAnswer)
      console.log(lastanswer)
    }
  },

}
</script>

<style lang="scss" scoped></style>
