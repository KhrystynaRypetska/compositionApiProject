<template>
  <div class="home">
    <h2>{{ appTitle }}</h2>
    <h1>{{ counterData.title }}</h1>
    <div>
      <button @click="decreaseCounter(1, $event)" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter(1, $event)" class="btn">+</button>
    </div>

    <p>This counter is {{ oddOrEven }}</p>

    <div class="edit">
      <h4>Edit counter title:</h4>
      <input v-model="counterData.title" type="text">
    </div>
  </div>
</template>

<script setup>
import {
  reactive,
  computed,
  watch,
  onBeforeMount,
  onMounted,
  onBeforeUnmount,
  onUnmounted,
  onActivated,
  onDeactivated
} from 'vue'

const appTitle = 'My Amazing Counter App'

const counterData = reactive({
  count: 0,
  title: 'My Counter'
})

watch(() => counterData.count, (newCount, oldCount) => {
  if(newCount === 20) {
    alert('Way to go! You made it to 20!!')
  }
})

const oddOrEven = computed(() => {
  if ( counterData.count % 2 === 0 ) return 'even'
  return  'odd'
})

const increaseCounter = (amount, e) => {
  counterData.count += amount
}

const decreaseCounter = (amount, e) => {
  counterData.count -= amount
}

onBeforeMount(() => {
  console.log('onBeforeMount')
})
onMounted(() => {
  console.log('onMounted')
})
onBeforeUnmount(() => {
  console.log('onBeforeUnmount')
})
onUnmounted(() => {
  console.log('onUnmount')
})
onActivated(() => {
  console.log('onActivated')
})
onDeactivated(() => {
  console.log('onDeactivated')
})


</script>


<style>
.home {
  text-align: center;
  padding: 20px;
}
.btn, .counter {
  font-size: 40px;
  margin: 10px;
}
.edit {
  margin-top: 60px;
}
</style>