<template>
    <div id="register">
        <input type="text" placeholder="E-Mail" v-model="email" required>
        <br>
        <br>
        <input type="password" placeholder="Password" v-model="password" required>
        <br>
        <br>
        <button @click="register">ISCRIVITI</button>
    </div>
</template>

<script>
    import { ref } from "vue"
    import { getAuth, createUserWithEmailAndPassword } from "firebase/auth"

    export default {
        data() {
            return {
                email: ref(""),
                password: ref("")
            }
        },
        methods: {
            register() {
                createUserWithEmailAndPassword(getAuth(), this.email, this.password)
                .then((data) => {
                    console.log(data)
                })
                .catch((error) => {
                    alert(error.message)
                })
            }
        }
    }

    const signInWithGoogle = () => {

    }
</script>

<style>
    #register {
        margin: auto;
        width: fit-content;
        padding: 100px;
        border: 2px solid black;
        border-radius: 25px;
    }

    #register input{
        width: 100%;
        height: 3vh;
    }

    #register label {
        text-align: left;
    }

    #register button {
        margin-bottom: 20px;
        height: 4vh;
        width: 100%;
    }
</style>