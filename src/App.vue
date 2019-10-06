<template>
  <div id="app">
    <Header />
    <UserList />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import UserList from './components/UserList.vue'

export default {
  name: 'app',
  components: {
    UserList,
    Header
  }
}
</script>

<style>
#app {

}
</style>
