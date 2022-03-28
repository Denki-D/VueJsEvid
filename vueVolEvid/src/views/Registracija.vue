<template>
  <h1>Kreirajte račun</h1>
  <p><input type="text"  placeholder="e-mail" v-model="email" /></p>
  <p><input type="password"  placeholder="Lozinka" v-model="password" /></p>
<p><button @click="registracija">Registracija</button></p>
</template>

<script setup>
import { ref } from "vue"
import { getAuth, createUserWithEmailAndPassword } from "firebase/auth"
import {useRouter} from 'vue-router'
import { error } from "console"
const email=ref("")
const password= ref("")
const router = useRouter()
const registracija = () => {
    createUserWithEmailAndPas
    .then((data))=> {
        console.log("Uspila rega");
        router.push('/probni');
    .catch ((error)) => console.log(error.code)
    }
}

</script>

<style>

</style>