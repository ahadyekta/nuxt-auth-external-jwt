<template>
  <section class="container">
    <div>
      <h1 class="title">
        login page
      </h1>
      <h2 class="subtitle">
        you see this beacuse you are not authenticated
      </h2>
      
      <div>
          <input type="text" value="SomeDummyUserName" />
          <br>
          <input type="password" value="SomeDummyPassword" />
          <br>
          <button  @click="postLogin" >Login</button>
      </div>
    </div>
  </section>
</template>

<script>
import Cookie from 'js-cookie'

export default {
  middleware: 'notAuthenticated',
  methods: {
    postLogin () {
      setTimeout(() => {
        const auth = {
          accessToken: 'someStringGotFromApiServiceWithAjax'
        }
        this.$store.commit('update', auth)
        Cookie.set('auth', auth)
        this.$router.push('/')
      }, 2000)
    }
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 30px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 22px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>