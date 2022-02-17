<template>
  <div>
    <div>Add a todo:</div>
    <input type="text" v-model="value">
    <button @click="addToDo">Add</button>
    <div>
      <div>My todo list:</div>
      <ToDoList :myProp="toDoListArray" @removeList="emptyList" @removeToDo="removeElement" />
    </div>
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
      toDoListArray: ["Go to dentist", "Feed the cat"],
      value: undefined
    }
  },
  methods: {
    addToDo() {
      this.toDoListArray.push(this.value)
      this.value = undefined
    },
    emptyList() {
      this.toDoListArray = []
    },
    removeElement(toDo) {
      this.toDoListArray.splice(this.toDoListArray.indexOf(toDo), 1)
    }
  }
}
</script>