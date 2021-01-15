<template>
  <div id="app">
    {{ user.username }} - {{ fullName }}
    <strong>Followers: </strong> {{ followers }}
    <button @click="followUser">Follow</button>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: "zahirsher",
        firstName: "Zahir",
        lastName: "Sher",
        email: "zakisher@gmail.com",
        isAdmin: true
      }
    }
  },

  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    }
  },

  methods: {
    followUser() {
      this.followers++;
    }
  },

  mounted() {
    this.followUser();
  },

  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.fullName} gained a follower!`)
      }
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 2rem;
  display: flex;
  flex-direction: column;
}
</style>
