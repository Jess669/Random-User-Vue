<template>
  <div>
    <CustomHeader/>
    <Person @fetchUser="fetchUser" :persons='this.users'/>
  </div>
</template>

<script>
import CustomHeader from './components/CustomHeader'
import Person from './components/Person'

export default {
  name: 'App',
  components: {
    CustomHeader,
    Person
  },
  data() {
    return {
      users: {}
    }
  },
  created() {
    this.fetchUser()
  },
  methods: {
    fetchUser() {
      fetch('https://randomuser.me/api/')
      .then(data => data.json())
      .then(res => this.addUser(res))
      .then(getUser => this.users = getUser)
      .catch(err => console.log(err))
    },
    addUser(res) {
      let user = {
        'id' : this.uniqueId(),
        'first' : res.results[0].name.first,
        'last' : res.results[0].name.last,
        'gender' : res.results[0].gender,
        'email' : res.results[0].email,
        'image' : res.results[0].picture.large
      }
      return user;
    },
    uniqueId() {
      return new Date().valueOf();
    }

  }
}
</script>
<!-- res.results[0].name.first -->
<!-- res.results[0].name.last -->
<!-- res.results[0].email -->
<!-- res.results[0].picture.large -->
<style>

@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;700&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  color: white;
  font-family: 'Poppins', sans-serif;
  text-decoration: none;
}

#app {
  min-height: 100vh;
  background-color: rgb(155, 163, 212);
}

</style>
