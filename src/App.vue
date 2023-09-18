<template>
<header class="absolute bottom-0 rotate-180">
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
</header>

<main class=" border h-screen flex items-center justify-center w-full px-4">
    <div class="flex flex-col gap-10 text-center w-full md:w-auto">
        <h1 class="text-4xl md:text-7xl font-bold block">Math Quiz App</h1>
        <BasicOperators v-if="!operators" @selectOperator="changeOperator" />
        <Quiz v-else :operators="operators" @back="clearOperator" />
    </div>
</main>
</template>

<script>
import BasicOperators from '@/components/BasicOperators.vue';
import Quiz from '@/components/Quiz.vue';
export default {
    components: {
        BasicOperators,
        Quiz
    },
    data() {
      return {
        operators: null,
      }
    },
    methods: {
      changeOperator(operator) {
        this.operators = operator
        // alert(this.operators)
      },
      clearOperator(){
        this.operators = null
      }
    },
}
</script>

<style scoped>
header {
    line-height: 1.5;
}
</style>



<!-- https://www.youtube.com/watch?v=y7dh6NrwlPI&t=1550s -->
