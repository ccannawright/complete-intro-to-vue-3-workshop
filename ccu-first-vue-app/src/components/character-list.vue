<script>
import { alertMessage } from '../composables/useState.js';
export default {
    setup() {
        
        return { alertMessage}
    },
    name: "CharacterList",
    props: {
        characters: {
            type: Array,
            required: true
        }
    },
    emit: ["favorite-character"]
}</script>
<template>
    <div>
    <h2> Main Characters</h2>
    <h3>{{ alertMessage }}</h3>
    <table>
        <thead>
            <tr>
                <th scope="col"> Name </th>
                <th scope="col"> Age </th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(character, index) in characters" :key="`character-${index}`">
                <th>{{ character.name }}</th>
                <th>{{ character.age }}</th>
                <th><button @click="this.$emit('favorite-character', character)"> Set As Favorite</button>
                </th>
            </tr>
        </tbody>
    </table>
</div>
</template>