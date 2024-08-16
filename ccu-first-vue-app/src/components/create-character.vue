<script>

export default {
    name: "CreateCharacter",
    emit: ['add-character']
   
}
</script>
<template>
    <div>
      <h2>Create A New Character</h2>
      <div class="createchar"> 
        <label for="name">what is their name? </label>
        <input type="text" name="name" id="characterName" required />
        <label for="age">What is the character's age?: </label>
        <input type="text" name="age" id="characterAge" required />
      </div>
      <div>
        <button @click='this.$emit("add-character")'> Add </button>
      </div>
    </div>
</template>
<style scoped>
label {
  padding-top: 10px;
    padding-right: 10px;
    padding-left: 10px;
    padding-bottom: 10px;
}
input {
  padding-top: 10px;
    padding-right: 10px;
    padding-left: 10px;
    padding-bottom: 10px;
}
</style>