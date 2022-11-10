<script setup>
import {useCounterStore} from '@/store/counter.js'
const userCounter = useCounterStore()
</script>

<template>
  <h1>Home: counter: {{userCounter.count}}</h1>
  <h2>Doble {{userCounter.double}}</h2>
  <button @click="userCounter.increment">Increment</button>
</template>
