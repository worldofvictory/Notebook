<script setup lang="ts">
import { ref } from 'vue';

const showModal = ref<boolean>(false)
const newNote = ref<string>("");
const notes = ref<T>([]);
const errorMessage = ref("");
function backgroundColor() {
  return "hsl(" + Math.random() * 360 + ", 100%, 75%)";
}


const addNote = () => { //aggiungiamo-card
  if(newNote.value.trim.length <10) {
    return errorMessage.value="Note needs to be 10 characters or more"
  }
  notes.value.push(
    {
      text: newNote.value,
      date: new Date(),
      id: Math.floor(Math.random() * 1000000),
      color: backgroundColor()
    });
  showModal.value = false;
  newNote.value = "";
  errorMessage.value = "";
}
</script>

<template>
  <main>
    <div v-if="showModal" class="overlay">
      <div class="modal">
        <textarea v-model.trim="newNote" name="note" id="note" cols="30" rows="10"></textarea>
        <p class="errorTxt" v-if="errorMessage"> {{ errorMessage }}</p>
        <button class="overlayBtn" @click="addNote">Add Note</button>
        <button class="closeBtn overlayBtn" @click="showModal = false">X</button>
      </div>
    </div>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button class="headerBtn" @click="showModal = true">+</button>
      </header>

      <div class="card-container">

        <div v-for="note in notes" 
        class="card" 
        :style="{ backgroundColor: note.color }"
        :key ="note.id">
          <p class="main-text">{{ note.text }}</p>
          <p class="date">{{ note.date.toLocaleDateString() }}</p>
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
  padding: 40px;
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

.headerBtn {
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

.card-container {
  display: flex;
  flex-wrap: wrap;
  padding: 0;
}

.card {
  width: 225px;
  height: 225px;
  background-color: #EEDEF6;
  padding: 10px;
  border-radius: 15px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-right: 60px;
  margin-bottom: 40px;
}

.date {
  font-size: 13px;
  font-weight: bold;
}

.overlay {
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.77);
  transform: translate(-50%, -50%);
  top: 50%;
  left: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 10;
}

.modal {
  width: 750px;
  background-color: #2F2F2F;
  border-radius: 10px;
  padding: 30px;
  position: relative;
  display: flex;
  flex-direction: column;
}

.overlayBtn {
  padding: 10px 20px;
  font-size: 20px;
  width: 100%;
  border: none;
  background-color: #EEDEF6;
  color: black;
  cursor: pointer;
  margin-top: 15px;
  border-radius: 3px;
}

.modal p {
  margin-left: auto;
  font-size: 20px;
  z-index: 100000;
  cursor: pointer;
}
.errorTxt {
  background-color: brown;
  margin-top: 7px;
}

textarea {
  /*width: 100%;*/
  height: 200px;
  padding: 5px;
  font-size: 20px;
  border-radius: 3px;
  color: white;
  background-color: rgba(0, 0, 0, 0.77);
}

.closeBtn {
  margin-top: 7px;
}
</style>
