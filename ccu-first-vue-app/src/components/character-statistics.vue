<script>
import { alertMessage } from '../composables/useState.js';
export default {
    setup() {
        return { alertMessage}
    },
    name: "CharacterStatistics",
    props: {
        characters: {
            type: Array,
            required: true
        }
    },
    computed: {
        howManyOld() {
            const statistics = {
                "old": 0,
                "young": 0
            }

            this.characters.forEach(character => {
                if (character.age > 30) {
                    statistics.old += 1
                }
                else {
                    statistics.young += 1
                }
            })
            return statistics;
        }
    },
    methods: {
        OldData () {
            if (this.howManyOld.old > 0) {
                this.alertMessage = "There are " + this.howManyOld.old + " old characters."
            }
            else {
                this.alertMessage = "There are no old characters."
            }
        }
    }
}
</script>
<template>
    <div>
        <h2>How Many Characters are Old?</h2>
        <h3> {{ alertMessage }}</h3>
        <button @click="OldData">Check Data</button>
        <p>{{ howManyOld }}</p>
    </div>
</template>