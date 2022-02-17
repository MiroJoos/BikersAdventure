<template>
    <ul>
        <ToDo v-for="item, itemIndex in myProp" :key="itemIndex" :toDo="item" @removeThisToDo="sendTheMessage" />
        <button @click="removeList">Empty list</button>
    </ul>
</template>

<script>
import ToDo from "./ToDo.vue"

export default {
    components: {
        ToDo
    },
    props: {
        myProp: {
            type: Array,
            default: () => []
        }
    },
    methods: {
        removeList() {
            this.$emit("removeList")
        },
        sendTheMessage(toDo) {
            this.$emit("removeToDo", toDo)
        }
    }
}
</script>