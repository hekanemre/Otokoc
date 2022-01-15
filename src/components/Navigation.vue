<template>
  <header class="title">
    <div class="home flex">
      <div class="user">Hakan Emre KESKİN</div>
      <div class="company">
      <span class="real">Otokoç</span> <span>Otomotiv</span> 
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'navigation',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
header{
  height: 10%;
  background-color:white;
  border-bottom: 3px solid  black;
}
.home {
  display: flex;
  justify-content: space-between;
}
.user{
  color: black;
  margin: 30px;
}
.company{
  margin: 30px;
}
.real{
  font-weight: bold;
}


</style>
