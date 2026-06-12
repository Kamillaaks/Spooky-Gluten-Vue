<script setup lang="ts">
import {ref} from 'vue'

const addPlace = ref({
    title: '',
    city: '',
    address: '',
    description: '',
})

const categories = [
    {
        name: 'Restaurant'
    },
    {
        name: 'Kafé'
    },
    {
        name: 'Bakeri'
    },
]

const selectedCategories = ref<number[]>([])

const coffeeRating = ref(0)
const foodRating = ref(0)

const stars = [1, 2, 3, 4, 5]

function setRating(type: 'coffee' | 'food', rating: number) {
    if (type === 'coffee') {
        coffeeRating.value = rating
    } else {
        foodRating.value = rating
    }
}

function goBack() {
    console.log('Tilbake')
}
</script>

<template>
    <div class="addPlacediv">
        <button class="registerButton" @click="goBack">
            Tilbake
        </button>
        <h2 class="addPlaceText">Legg til sted</h2>
    </div>

    <div class="addPlaceInputSection">
        <h2 class="addPlaceText">Navn</h2>
        <input
            v-model="addPlace.title"
            class="addPlaceInput"
            type="text"
            placeholder="Navn på sted"
        >
        <br>
        <h2 class="addPlaceText">By</h2>
        <input
            v-model="addPlace.city"
            class="addPlaceInput"
            type="text"
            placeholder="By"
        >
        <br>
        <h2 class="addPlacetext"> Adresse</h2>
        <input
            v-model="addPlace.address"
            class="addPlaceInput"
            type="text"
            placeholder="Adresse"
        >
        <br>
        <h2 class="addPlaceText">Beskrivelse</h2>
        <input
            v-model="addPlace.description"
            class="addPlaceinput"
            type="text"
            placeholder="Beskrivelse"
        >
    </div>

    <div class="addPlaceCategorySection">
        <h2 class="addPlaceText">Velg kategorier</h2>
        <div
            v-for="(category, index) in categories"
            :key="index"
        >
            <input
                type="checkbox"
                :value="index"
                v-model="selectedCategories"
            >
            {{ category.name }}
        </div>
    </div>

    <div>
        <h2 class="addPlaceText">Rating</h2>
        <div class="addPlaceRatingSection">
            <div>
                <span>Kaffe: </span>

                <button
                    v-for="star in stars"
                    :key="`coffee-${star}`"
                    class="star"
                    @click="setRating('coffee', star)"
                >
                    {{ star <= coffeeRating ? '★' : '☆' }}
                </button>
            </div>

            <div>
                <span>Mat: </span>

                <button
                    v-for="star in stars"
                    :key="`food-${star}`"
                    class="star"
                    @click="setRating('food', star)"
                >
                    {{ star <= foodRating ? '★' : '☆' }}
                </button>
            </div>
        </div>
    </div>
</template>

<style scoped>
.star {
    background: none;
    border: none;
    cursor: pointer;

    font-size: 1.5rem;
}

</style>