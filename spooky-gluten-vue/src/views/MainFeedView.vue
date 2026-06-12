<script setup lang="ts">
import {ref} from 'vue'

const search = ref('')

const isAdmin = true

const places = [
    {
        id: 1,
        title: 'Glutenfri Café',
        image: 'https://picsum.photos/200',
        city: 'Tromsø',
        address: 'Storgata 1',
        rateFood: 4,
    },
    {
        id: 2,
        title: 'Pizza plass',
        image: 'https://picsum.photos/201',
        city: 'Bodø',
        address: 'Sentrumsgata 5',
        rateFood: 5,
    },
]

function goToAddPlace() {
    console.log('Gå til legg til sted')
}

function goToLogin() {
    console.log('Gå til login')
}

function searchFeed() {
    console.log('Søk etter:', search.value)
}

function deleteItem(id: number) {
    console.log('Slett', id)
}

function goToPlacePage(id: number) {
    console.log('Gå til side', id)
}
</script>

<template>
    <main>
        <div class="feedControls">
            <button class="mainFeedButton" @click="goToAddPlace">
                Legg til sted
            </button>

            <button class="mainFeedButton" @click="goToLogin"> 
                Logg inn
            </button>

            <br>

            <input
                v-model="search"
                class="mainFeedInput"
                placeholder="Søk by/adresse"
                type="text"
            >

            <button class="search-button" @click="searchFeed">
                🔍
            </button>
        </div>

        <div id="feedDiv">
            <div
                v-for="place in places"
                :key="place.id"
            >

            </div>
        </div>

        <div
            v-for="place in places"
            :key="place.id"
        >

            <button
                v-if="isAdmin"
                class="deleteBtn"
                @click="deleteItem(place.id)"
            >
                Slett
            </button>

            <div
                class="feedItem"
                @click="goToPlacePage(place.id)"
            >
                <div class="filteredListImg">
                    <img
                        class="filteredListImg"
                        :src="place.image"
                        :alt="place.title"
                    >
                </div>

                <div class="filteredListInfo">
                    <b>{{ place.title }}</b>
                    {{ '⭐'.repeat(place.rateFood) }}
                    <br>
                    {{ place.city }}
                    {{ place.address }}
                </div>
            </div>
        </div>
    </main>
</template>

<style scoped>
.search-button {
    background-color: #5B8AB3;
    border-width: 0;
    border-radius: 15px;
    padding: 3px;
}
</style>