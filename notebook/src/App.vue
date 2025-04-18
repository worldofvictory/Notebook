<script setup lang="ts">

</script>

<template>
  <main>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button class="">+</button>
      </header>
      <div class="card-container">
        <div class="card">
          <p class="main-text">lorem</p>
          <p class="date">19/04/2025</p>
        </div>
        <div class="card">
          <p class="main-text">lorem</p>
          <p class="date">19/04/2025</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.container {
  margin: 0 auto;
  max-width: 1000px;
  padding: 10px;
  background-color: #f2f2f2;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h1 {
  font-weight: bold;
  font-size: 75px;
  
  margin: 0;
  margin-bottom: 25px;
}

button {
  border: none;
  padding: 10px;
  width: 50px;
  height: 50px;
  cursor: pointer;
  background-color: #EEDEF6;
  border-radius: 100%;
  color: black;
  font-size: 20px;
}
.card-container{
  display: flex;
  flex-wrap: wrap;
}
.card {
  width: 225px;
  height: 225px;
  background-color: #FEE1B6;
  padding: 10px;
  border-radius: 15px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-right: 20px;
margin-bottom: 20px;
}
.date{
  font-size: 13px;
  font-weight: bold;
}
</style>
