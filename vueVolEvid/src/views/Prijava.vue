<template>
  <h1>Prijavite se</h1>
  <p><input type="text"  placeholder="e-mail" v-model="email" /></p>
  <p><input type="password"  placeholder="Lozinka" v-model="password" /></p>
<p><button @click="prijava">Prijava</Putton></p>
</template>

<script setup>
import { ref } from "vue"
import { getAuth, signInWithEmailAndPassword } from "firebase/auth"
import {useRouter} from 'vue-router'
import { error } from "console"
const email=ref("")
const password= ref("")
const router = useRouter()
const prijava = () => {
    signInWithEmailAndPassword(auth(), email.value, password.value)
    .then((data))=> {
        console.log("Uspješna prijava");
        router.push('/probni');
    .catch ((error)) => console.log(error.code)
    }
}

</script>

<style>

</style>