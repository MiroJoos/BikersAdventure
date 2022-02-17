<template>
    <li> 
        {{ toDo }} 
        <button @click="remove">Remove To Do</button>
    </li>
</template>

<script>
export default {
    props: {
        toDo: {
            type: String,
            default: ""
        }
    },
    methods: {
        remove() {
            this.$emit("removeThisToDo", this.toDo)
        }
    }
}
</script>