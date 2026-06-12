<script setup lang="ts">
const selectedPlace = {
    title: 'Glutenfri Café',
    image: 'https://picsum.photos/400',
    address: 'Storgata 1',
    rateCoffee: 4,
    rateFood: 5,
    description: 'Koselig café med glutenfrie alternativer.',
    categories: ['Restaurant', 'kafé'],
}

function goBack() {
    console.log('tilbake til main feed')
}

</script>

<template>
    <div class="placePageDiv">

        <h1 class="title">
            {{ selectedPlace.title }}
        </h1>

        <p id="category">
            <span
                v-for="category in selectedPlace.categories"
                :key="category"
            >
                 ♡{{ category }}                
            </span>
        </p>

        <img
            class="placePageImg"
            :src="selectedPlace.image"
            alt="Bilde av plassen"
        >

        <p class="registerText">
            {{ selectedPlace.address }}
        </p>

        <p id="rating">
            ☕ {{ '⭐'.repeat(selectedPlace.rateCoffee) }}
            <br>
            🍽️ {{ '⭐'.repeat(selectedPlace.rateFood) }}
        </p>

        <p class="registerText">
            Beskrivelse
        </p>

        <p id="description">
            {{ selectedPlace.description }}
        </p>

        <button
            class="registerButton"
            @click="goBack"
        >
            Tilbake
        </button>
    </div>
</template>