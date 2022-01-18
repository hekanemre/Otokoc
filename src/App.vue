<template>
  <div>
    <div v-if="loginBar" class="login">
      <div class="User">Kullanıcı Adı veya Parola</div>
      <input type="text" class="username" value="Otokoç">
      <div class="Pass">Parola</div>
      <input type="password" class="password" value="Otokoç34">
      <div class="button"><button @click="clicked" class="submit">Login</button></div>
    </div>
    <div class="app flex-column">
      <Navigation
      v-if="NavigationBar"/>
      <div class="app-content flex flex-coloumn">
          <router-view 
          v-if="HomeBar"/>     
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Navigation from '@/components/Navigation.vue'

export default {
  data: ()=>{
    return {
      NavigationBar: false,
      HomeBar: false,
      loginBar: true,
      userName: '',
      Password: '',
    }
  },
  methods:{
    clicked(){
      this.NavigationBar = true
      this.HomeBar = true
      this.loginBar = false
    }
  },
  components: {
    Navigation,
  }
}
</script> 

<style>
.login{
  margin-left: 780px;
  margin-top: 300px;
}
.User,
.username,
.Pass,
.password,
.button{
  margin-bottom: 10px;
}
.User,
.Pass{
  font-weight: bold;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
.app{
  min-block-size: 100vh; 
  @media (min-width: 900px;){
    flex-direction: row;
  }
}
.app-content{
    padding: 0 20px;
    flex: 1;
    position: relative; 
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
button{
  cursor: pointer;
}
</style>
