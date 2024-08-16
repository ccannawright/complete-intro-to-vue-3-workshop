<script>
import CharacterStatistics from './components/character-statistics.vue';
import CreateCharacter from './components/create-character.vue';
import FavoriteCharacters from './components/favorite-characters.vue';
import CharacterList from './components/character-list.vue';
import MainWrapper from './components/main-wrapper.vue';

export default {
  components: { CreateCharacter, FavoriteCharacters, CharacterStatistics, CharacterList, MainWrapper },
  // Can also write as: data: () => ({})
  data() {
    return {
      tvShowName: "Parks and Recreation",
      listOfCharacters: [{ "name": "April Ludgate", "age": 20 }, { "name": "Ron Swanson", "age": 55 }, { "name": "Leslie Knope", "age": 40 }, { "name": "Ben Wyatt", "age": 41 }, { "name": "Andy Dwyer", "age": 29 }, { "name": "Ann Perkins", "age": 28 }, { "name": "lil Sebastian", "age": 5 }],
      listFaves: []
    }
  },
  methods: {
    setFavorite(character) {
      if (this.listFaves.includes(character)) {
        return
      }
      this.listFaves.push(character)
    },
    addCharacter() {
        this.listOfCharacters.push({ 
          "name": document.getElementById("characterName").value,
          "age": document.getElementById("characterAge").value
        })
      },
  }

} 
</script>

<template>
  <main-wrapper>
    <template v-slot:header>
      <h1 v-if="tvShowName.length % 2 === 0"> My Favorite Show is {{ tvShowName }} </h1>
      <h1 v-else> My least favorite show is {{ tvShowName }} </h1>
    </template>
   <template v-slot:main>
    <character-list :characters="listOfCharacters" @favorite-character="setFavorite"/>
    <character-statistics :characters="listOfCharacters"/>
    <favorite-characters :faveCharacters="listFaves"/>
   </template>
   <template v-slot:footer>
    <create-character :characters="listOfCharacters" @add-character="addCharacter"/>
   </template>
  </main-wrapper>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.title {
    
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
 
}
</style>
