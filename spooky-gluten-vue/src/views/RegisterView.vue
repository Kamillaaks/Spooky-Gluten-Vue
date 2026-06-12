<script setup lang="ts">
const user = {
    username: '',
    password: '',
    repeatPassword: '',
    email: '',
}

function verifyRegistration() {
    console.log('Sjekk')
}

function goBack() {
    console.log('tilbake')
}
</script>

<template>
    <div class="registerDiv">
        <button
            class="registerButton"
            @click="goBack"
        >
        Tilbake
        </button>
        <img
            src="https://picsum.photos/240"
            alt="Logo"
        >
        <h1 class="title">Lag ny bruker</h1>
        <div>
            <h2 class="registerText">Brukernavn</h2>
            <input
                class="registerInput"
                placeholder="Ditt brukernavn"
                v-model="user.username"
            >
            <div id="usernameError"></div>

            <h2 class="registerText">Mailadresse</h2>
            <input
                class="registerInput"
                placeholder="Din mailadresse"
                v-model="user.email"
            >

            <h2 class="registerText">Passord</h2>
            <input
                class="registerInput"
                placeholder="Ditt passord"
                type="password"
                v-model="user.password"
            >

            <input
                class="registerInput"
                placeholder="Gjenta passord"
                type="password"
                v-model="user.repeatPassword"
            >

            <div id="repeatPwError"></div>
        </div>
        <button class="registerButton" @click="verifyRegistration">
            Lag ny bruker
        </button>
    </div>
</template>