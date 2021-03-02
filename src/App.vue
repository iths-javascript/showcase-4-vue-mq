<template>
  <div id="app">
    <h1>{{$mq}}</h1>
    <section :class="$mq">
      <UserCard v-for="user in firstFour" :key="user.email" :user="user" />
    </section>
  </div>
</template>

<script>
import UserCard from '@/components/UserCard'
import data from '@/assets/users.json'

export default {
  components: {UserCard},
  data(){return {users: data.results}},
  name: 'App',
  computed: {
    firstFour(){
      return this.users.filter((_,i) => i < 4)
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

section{
  justify-content: center;
  margin: auto;
  max-width: 1000px;

  &.laptop, &.desktop{
    display: grid;
    grid-template-columns: repeat(2, 1fr);
  }

  &.mobile{
    display: flex;
    flex-direction: column;
  }

}
</style>
