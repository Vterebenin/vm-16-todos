<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Главная</router-link> |
      <router-link to="/projects">Проекты</router-link> |
      <router-link to="/about">Контакты</router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>
  import github from 'octonode'
  export default {
    name: "App",
    data() {
      return {
        api: process.env.VUE_APP_GITHUB_API
      }
    },
    async mounted() {
      const client = github.client()
      const ghuser = client.user('vterebenin')
      const userInfo = await ghuser.infoAsync()
      console.log(userInfo)
    }
  }
</script>

<style lang="scss">
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }
  #nav {
    padding: 30px;
    a {
      font-weight: bold;
      color: #2c3e50;
      &.router-link-exact-active {
        color: #42b983;
      }
    }
  }
</style>
