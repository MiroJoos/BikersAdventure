<template>
    <div id="login">
        <input type="text" placeholder="E-Mail" v-model="email" required>
        <br>
        <br>
        <input type="password" placeholder="Password" v-model="password" required>
        <br>
        <br>
        <p v-if="errorMsg"> {{ errorMsg }} </p>
        <br>
        <button @click="login">ACCEDI</button>
        <br>
        <p>Non hai ancora un account?&nbsp;<a href="/register">Registrati</a></p>
    </div>
</template>

<script>
    import { ref } from "vue"
    import { getAuth, signInWithEmailAndPassword } from "firebase/auth"

    export default {
        data() {
            return {
                email: ref(""),
                password: ref(""),
                errorMsg: ref("")
            }
        },
        methods: {
            login() {
                signInWithEmailAndPassword(getAuth(), this.email, this.password)
                .then((data) => {
                    console.log("Successfully signed in")
                })
                .catch((error) => {
                    console.log(error.code)
                    console.log(error.message)

                    switch (error.code) {
                        case "auth/invalid-email":
                            errorMsg.value = "E-Mail non corretta"
                            break
                        case "auth/user-not-found":
                            errorMsg.value = "Questo utente non esiste"
                            break
                        case "auth/wrong-password":
                            errorMsg.value = "Password non corretta"
                            break
                    }
                })
            }
        }
    }

    const signInWithGoogle = () => {

    }
</script>

<style>
    #login {
        margin: auto;
        width: fit-content;
        padding: 100px;
        border: 2px solid black;
        border-radius: 25px;
    }

    #login input{
        width: 100%;
        height: 3vh;
    }

    #login label {
        text-align: left;
    }

    #login button {
        margin-bottom: 20px;
        height: 4vh;
        width: 100%;
    }
</style>