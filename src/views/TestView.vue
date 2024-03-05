<script setup>
import Test from '../components/Test.vue'
import { onBeforeMount, onMounted, ref, reactive, computed,watch } from 'vue'


const author = reactive({
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
})




var publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? 'Yes' : 'No'
})

const fullName = computed({
  // getter
  get() {
    return author.name;
  },
  // setter
  set(newValue) {

    author.name = newValue;
  }
})

fullName.value = "melke"


const isActive = ref(false);
const hasError = ref(false);

onMounted(() => {
  console.log(`the component TestView is now mounted.`)
})


// let myVar = ref(0)

// setInterval(() => {
//   myVar.value++;
// }, 1000);


// let date= ref(0);

// setInterval(() => {
//   date.value = new Date().getSeconds();
// }, 1000);


// watch(date, (newX) => {
//   console.log(`x is ${newX}`)
// })



// setInterval(() => {
//   let d = new Date()

//   console.log(d)
// }, 1000);

const input = ref(null)



onMounted(() => {
  input.value.focus()
  input.value.style.backgroundColor = "green"
  input.value.style.border = "5px solid red"

  console.log(input.value.innerHTML)
})
</script>


<template>
    <div class="test">
      <h1>this is a TestView</h1>

      <h2>Author:{{ author.name }}</h2>
      <p>Has published books:</p>
<span>{{ publishedBooksMessage}}</span>

<div :class="{ active: isActive ,'text-danger': hasError} ":style="{ display: ['-webkit-box', '-ms-flexbox', 'flex'] }"></div>

<button @click="isActive = !isActive; hasError = !hasError">Change</button>

<!-- <h1>{{ date }}</h1> -->

<button ref="input">refInput</button>

<Test/>
    </div>

 
  </template>
  
  <style>
  @media (min-width: 1024px) {
    .test {
      min-height: 100vh;
      display: flex;
      align-items: center;
      flex-direction: column;
    }
  }

  .active{
    width: 20px;
    height: 20px;
    background-color: red;
  }

  .text-danger{
    border: 2px solid yellow;
  }
  </style>