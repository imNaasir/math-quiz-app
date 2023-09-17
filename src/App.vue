<template>
<header class="absolute bottom-0 rotate-180">
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
</header>

<main class="w-screen border h-screen flex items-center justify-center">
    <div class="flex flex-col gap-10 text-center">
        <h1 class="text-7xl font-bold block">Math Quiz App</h1>
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
