<template>
  <h1>Prijavite se</h1>
  <p><input type="text"  placeholder="e-mail" v-model="email" /></p>
  <p v-if="errMsg">{{ errMsg }}</p>
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
const errMsg = ref("")
const router = useRouter()
const prijava = () => {
    signInWithEmailAndPassword(auth(), email.value, password.value)
    .then((data))=> {
        console.log("Uspješna prijava");
        router.push('/probni');
    .catch ((error)) => { 
      console.log(error.code);
      switch (error.code){
        case "auth/invalid-email":
          errMsg.value = "Krivi e-mail";
          break;
        case "auth/user-not-found":
          errMsg.value = "Nije pronađen korisnik s ovim e-mailom";
          break;
        case "auth/wrong-password":
          errMsg.value = "Krivo unesena lozinka";
          break;
        default:
          errMsg.value = "Krivi e-mail ili lozinka";
          break;
      }
      alert(error.message)
    }
}

</script>

<style>

</style>