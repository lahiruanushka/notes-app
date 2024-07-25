<script setup>
  import {ref} from "vue";

  const isModalOpen = ref(false);
  const newNote = ref("");
  const notes = ref([])

  const openModal = () => {
    isModalOpen.value = true;
  }

  const closeModal = () => {
    isModalOpen.value = false;
  }

function getRandomColor() {
  const hue = Math.random() * 360;
  const color = `hsl(${hue}, 100%, 75%)`;
  return color;
}

  const addNote = () => {
    notes.value.push({
      id: Math.floor(Math.random() * 1000000),
      text: newNote.value,
      date: new Date(),
      backgroundColor: getRandomColor()
    });

    isModalOpen.value = false;
    newNote.value = "";
  } 
</script>

<template>
  <main>
    <div class="container">
      <header class="header">
        <h1>Notes</h1>
        <button class="add-button" @click="openModal">+</button>
      </header>
      <div class="cards-container">
        <div class="card">
          <p class="main-text">Lorem ipsum dolor sit amet consectetur adipisicing elit. Placeat nesciunt architecto hic. Sit dignissimos repudiandae quae commodi reprehenderit nihil dolores explicabo debitis. Nam, nostrum architecto dolore. Dolore laboriosam fugit blanditiis.</p>
          <p class="date">07/20/2022</p>
        </div>
                <div class="card">
          <p class="main-text">Lorem ipsum dolor sit amet consectetur adipisicing elit. Placeat nesciunt architecto hic. Sit dignissimos repudiandae quae commodi reprehenderit nihil dolores explicabo debitis. Nam, nostrum architecto dolore. Dolore laboriosam fugit blanditiis.</p>
          <p class="date">07/20/2022</p>
        </div>
      </div>
    </div>
    
    <div v-if="isModalOpen" class="modal-overlay">
      <div class="modal">
        <h2>Create Note</h2>
        <textarea 
          placeholder="Enter your note here..." 
          cols="30" 
          rows="10"
          v-model="newNote"
          ></textarea>
        <button class="modal-button" @click="addNote">Save</button>
        <button @click="closeModal" class="modal-button cancel-button">Cancel</button>
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, #ece9e6, #ffffff);
  font-family: Arial, sans-serif;
}

.container {
  max-width: 600px;
  width: 100%;
  padding: 20px;
  background: white;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

h1 {
  font-weight: bold;
  font-size: 2rem;
  color: #333;
}

.add-button {
  background: #007bff;
  border: none;
  color: white;
  padding: 10px 20px;
  font-size: 1.5rem;
  border-radius: 5px;
  cursor: pointer;
  transition: background 0.3s;
}

.add-button:hover {
  background: #0056b3;
}

.cards-container {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.card {
  background: #f9f9f9;
  padding: 15px;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.main-text {
  font-size: 1.2rem;
  color: #333;
  margin-bottom: 10px;
}

.date {
  font-size: 0.9rem;
  color: #666;
  text-align: right;
}

/* Modal Styles */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal {
  background: white;
  padding: 20px;
  border-radius: 10px;
  width: 90%;
  max-width: 500px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.modal h2 {
  margin-top: 0;
  font-size: 1.5rem;
  color: #333;
}

textarea {
  width: 95%;
  height: 100px;
  margin-bottom: 20px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 1rem;
  resize: none;
}

.modal-button {
  background: #007bff;
  border: none;
  color: white;
  padding: 10px 20px;
  font-size: 1rem;
  border-radius: 5px;
  cursor: pointer;
  margin-right: 10px;
  transition: background 0.3s;
}

.modal-button:hover {
  background: #0056b3;
}

.cancel-button {
  background: #ccc;
}

.cancel-button:hover {
  background: #999;
}
</style>
