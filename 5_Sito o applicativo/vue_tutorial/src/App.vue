<template>
  <div>
    <div>Calculate VTA</div>
    <input type="number" v-model="value">
    <p> {{ calculate }} </p>
    <p> {{ filterToDo }} </p>
  </div>
</template>

<script>
import ToDoList from "./components/ToDoList.vue"

export default {
  components: {
    ToDoList
  },
  data() {
    return {
      value: 0,
      toDoList: [{
        id: 1,
        text: "Feed the dog"
      },{
        id: 2,
        text: "Feed the cat"
      },{
        id: 3,
        text: "Feed the fish"
      }]
    }
  },
  computed: {
    calculate() {
      return `$ ${parseInt(this.value * 20 / 100)}`
    },
    filterToDo() {
      return this.toDoList.filter(toDo => {
        return toDo.id < 3
      })
    }
  },
  created() {
    this.value = 2
  }
}
</script>