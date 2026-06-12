<script setup lang="ts">
import {ref} from 'vue'

const currentUser = ref<string | null>(null)

const login = ref({
    username: '',
    password: '',
    anonymous: false,
})

function changePage() {
    console.log('Gå til registrering')
}

function loginUser() {
    console.log(login.value)
}

function loginAsAnonymous() {
    currentUser.value = 'Spooky'
}

function logout() {
    currentUser.value = null
}
</script>

<template>
    <div v-if="currentUser === null">
        <div class="showLoginPage">
            <img
                src="https://picsum.photos/240"
                alt="Logo"
            >
            <h2 class="title">Logg inn</h2>
            <div class="showLoginPage">
                <input
                    class="loginInput"
                    type="text"
                    placeholder="Brukernavn"
                    v-model="login.username"
                >
                <input
                    class="loginInput"
                    type="password"
                    placeholder="passord"
                    v-model="login.password"
                >
            </div>
            <div>
                <button
                    class="showLoginButton"
                    @click="changePage"
                >
                    Registrer ny bruker
                </button>  

                <button
                    class="showLoginButton"
                    @click="loginUser"
                >
                    Logg inn
                </button>
            </div>
            <div class="anonymousCheck">
                <label class="checkbox">
                    <input
                        v-model="login.anonymous"
                        class="checkbox__trigger visuallyhidden"
                        type="checkbox"
                        id="anonymousCheck"
                    >
                    <p class="checkbox__textwrapper">Vis meg som Spooky</p>
                </label>
            </div>
            <div>
                <button
                class="showLoginButtonAnonymous"
                @click="loginAsAnonymous()"
                >
                Fortsett uten brukernavn
                </button>
            </div>
            <div id="loginErrorMessage"></div>
        </div>
    </div>
    <div v-else>
        <div class="showLoginPage">
            <h2 class="showLoginHeader">
                Velkommen {{ currentUser }}
            </h2>
            <button
                class="showLoginButton"
                @click="logout"
            >
            Logg ut
            </button>
        </div>
    </div>
</template>