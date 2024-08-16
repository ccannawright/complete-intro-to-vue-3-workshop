<script>

export default {
    name: "FavoriteCharacters",
    props: {
        faveCharacters: {
            type: Array,
            required: true
        }
    }
}
</script>
<template>
    <div>
      <h2 v-if="faveCharacters.length === 0"> I have no favorite characters
      </h2>
      <h2 v-else> My favorite characters are:
      <ul>
        <li v-for="(fave, index) in faveCharacters" :key="`fave-${index}`"> {{ fave }}</li>
      </ul>
    </h2>
    </div>
</template>