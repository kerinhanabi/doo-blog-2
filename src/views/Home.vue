<template>
  <div class="home">
      <h1>Home</h1>
      <h2>Refs</h2>
      <p>{{ dooOne.name }} - {{ dooOne.age }}</p>
      <button @click="updateDooOne">Update Doo One</button>

      <h2>Reactive</h2>
      <p>{{ dooTwo.name }} - {{ dooTwo.age }} - {{ nameTwo }}</p>
      <button @click="updateDooTwo">Update Doo Two</button>
  </div>
</template>

<script>
import { ref, reactive } from 'vue';

export default {
  name: 'Home',

  setup() {
    // using ref way
    const dooOne = ref({ name: 'mario', age: 30 })

    // using reactive way
    const dooTwo = reactive({ name: 'daisy', age: 35 })

    // if case 2
    const nameOne = ref('AAA')
    const nameTwo = reactive('BBB')

    // using ref: lets make a function: a click event
    const updateDooOne = () => {
      dooOne.value.age = 40
    }

    // using reactive: lets make a function: a click event, can directly use .age without .value infront of it
    const updateDooTwo = () => {
      dooTwo.age = 45

      //if case 2 the ways below won't work cos nameTwo reactive is primitive value
      //nameTwo = 'CCC'
      //nameTwo = reactive('CCC')
    }

    return { dooOne, updateDooOne, dooTwo, updateDooTwo, nameTwo, nameOne }
  }
}
</script>
