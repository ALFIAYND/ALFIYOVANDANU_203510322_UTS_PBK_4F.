<script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div>
    
  </div>
  <HelloWorld msg="ALFIYOVANDANU" />
</template>


<style scoped>
/* Warna latar belakang untuk div utama */
div {
  background-color: #f0f0f0;
  padding: 20px;
}

/* Gaya untuk judul */
h1 {
  color: #333;
  font-size: 24px;
  margin-bottom: 20px;
}

/* Gaya untuk tombol tambah */
button {
  padding: 8px 16px;
  border: none;
  background-color: #007bff;
  color: #fff;
  cursor: pointer;
  border-radius: 4px;
}

button:hover {
  background-color: #0056b3;
}

/* Gaya untuk input teks */
input[type="text"] {
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

/* Gaya untuk tabel */
table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  padding: 12px;
  border-bottom: 1px solid #ddd;
  text-align: left;
}

/* Warna latar belakang untuk baris tabel saat dihover */
tr:hover {
  background-color: #e0e0e0;
}

/* Gaya untuk kegiatan yang telah selesai */
.completed {
  text-decoration: line-through;
  color: #888;
}

/* Gaya untuk div card */
.card {
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

/* Gaya untuk tombol di dalam div card */
.card button {
  margin-right: 10px;
}

/* Gaya untuk tombol filter */
.card button:nth-child(3) {
  background-color: #28a745;
}

.card button:nth-child(3):hover {
  background-color: #218838;
}

/* Gaya untuk tombol batal */
.card button:nth-child(2) {
  background-color: #dc3545;
}

.card button:nth-child(2):hover {
  background-color: #c82333;
}
</style>
