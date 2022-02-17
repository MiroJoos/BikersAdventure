<template>
    <div id="login">
        <label for="email">E-Mail:</label>
        <br>
        <input type="text" v-model="email" required>
        <br>
        <br>
        <label for="password">Password:</label>
        <br>
        <input type="password" v-model="password" required>
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
    const email = ref("")
    const password = ref("")
    const errorMsg = ref("")

    export default {
        methods: {
            login() {
                signInWithEmailAndPassword(getAuth(), email.value, password.value)
                .then((data) => {
                    console.log("Successfully signed in")
                })
                .catch((error) => {
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