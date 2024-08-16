<script>
import UsersPage from './components/users-page.vue'
export default {
  components: {UsersPage },
  name: 'App',
  data() {
    return {
      currentComponent: 'users-page',
      navItems: ['users', 'posts', 'comments']
    }
  },
  methods: {
    changeComponent(component) {
      this.currentComponent = `${component}-page`
    }
  }
}
</script>

<template>
<div>
  <nav>
    <ul>
      <li v-for="(item, index) in navItems" :key="`nav-${index}`"><button @click="changeComponent(item)">{{item}}</button></li> 
    </ul>
  </nav>
  <Suspense>
    <component :is="currentComponent" />
    <template #fallback>
      {{ currentComponent }} is loading...
    </template>
  </Suspense>
</div>
</template>

<style scoped>
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
</style>