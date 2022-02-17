<template>
  <div>
    <div v-for="(item, itemIndex) in people" :key="itemIndex">
      <p> {{ item.name }}: {{ item.age }} anni</p>
      <button @click="increaseAges(item)">Increase my age</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      people: [{
        name: "Samuel",
        age: 19
      }, {
        name: "Antonio",
        age: 20
      }, {
        name: "Armando",
        age: 21
      }]
    }
  },
  methods: {
    increaseAges(person) {
      person.age++
    }
  }
}
</script>