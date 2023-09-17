<template>
  <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
    <button @click="$emit('selectOperator', '+')" class="bg-[#1a434d] p-4 h-[80px] text-white align-top rounded text-2xl leading-6 ">Addition <br> +</button>
    <button @click="$emit('selectOperator', '-')" class="bg-[#1a434d] p-4 h-[80px] text-white align-top rounded text-2xl leading-6 ">Subtraction <br> -</button>
    <button @click="$emit('selectOperator', '*')" class="bg-[#1a434d] p-4 h-[80px] text-white align-top rounded text-2xl leading-6 ">multiplication <br> ×</button>
    <button @click="$emit('selectOperator', '/')" class="bg-[#1a434d] p-4 h-[80px] text-white align-top rounded text-2xl leading-6 ">divition <br> ÷</button>
  </div>
</template>

<script>
  export default {
    name: "BasicOperators",

    
  }
</script>

<style lang="scss" scoped>

</style>