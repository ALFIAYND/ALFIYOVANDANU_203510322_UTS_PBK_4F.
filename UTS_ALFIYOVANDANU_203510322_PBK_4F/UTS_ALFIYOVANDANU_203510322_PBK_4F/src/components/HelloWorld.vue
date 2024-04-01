<template>
  <div>
    <h1>{{ msg }}</h1>
    <div class="add-activity">
      <h2>DAFTAR KEGIATAN </h2>
      <input type="text" v-model="newActivityName" placeholder="Tambah kegiatan baru...">
      <button @click="addNewActivity">Tambah</button>
    </div>
    <br>
    <div class="card">
      <button @click="addActivity">Tambah Kegiatan</button>
      <button @click="cancelActivity">Batal</button>
      <button @click="toggleFilter">Filter Kegiatan Belum Selesai ({{ showCompleted ? 'Ditampilkan' : 'Disembunyikan' }})</button>
    </div>
    <br>
    <table class="activity-table">
      <thead>
        <tr>
          <th>Kegiatan</th>
          <th>Status</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(activity, index) in filteredActivities" :key="index" @click="toggleActivity(index)" :class="{ 'completed': activity.completed }">
          <td>{{ activity.name }}</td>
          <td>{{ activity.completed ? 'Selesai' : 'Belum Selesai' }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const msg = 'ALFI YOVANDANU '
const activities = ref([
  { name: 'Game', completed: false },
  { name: 'futsal', completed: true },
  { name: 'membaca', completed: false },
])

const showCompleted = ref(false)
const newActivityName = ref('')

function addActivity() {
  const activityName = prompt('Masukkan nama kegiatan:')
  if (activityName) {
    activities.value.push({ name: activityName, completed: false })
  }
}

function cancelActivity() {
  const activityIndex = prompt('Masukkan nomor kegiatan yang ingin dibatalkan:')
  if (activityIndex && !isNaN(activityIndex)) {
    activities.value.splice(activityIndex, 1)
  }
}

function toggleActivity(index) {
  activities.value[index].completed = !activities.value[index].completed
}

function toggleFilter() {
  showCompleted.value = !showCompleted.value
}

function addNewActivity() {
  const trimmedName = newActivityName.value.trim()
  if (trimmedName) {
    activities.value.push({ name: trimmedName, completed: false })
    newActivityName.value = ''
  }
}

const filteredActivities = computed(() => {
  if (showCompleted.value) {
    return activities.value
  } else {
    return activities.value.filter(activity => !activity.completed)
  }
})
</script>

<style scoped>
table.activity-table {
  width: 100%;
  border-collapse: collapse;
  background-color: black; /* Mengubah latar belakang tabel menjadi hitam */
  color: white; /* Mengubah warna teks menjadi putih */
}

th, td {
  padding: 8px;
  border-bottom: 1px solid #ddd;
  text-align: left;
}

th {
  border-top: 1px solid #ddd;
}

tr:hover {
  background-color: #333; /* Mengubah warna latar belakang saat dihover */
  cursor: pointer;
}

.add-activity {
  margin-bottom: 20px;
}

.completed {
  text-decoration: line-through;
}
</style>
