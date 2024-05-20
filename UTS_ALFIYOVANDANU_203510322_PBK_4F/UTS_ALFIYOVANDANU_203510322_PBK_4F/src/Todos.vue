<template>
  <div class="Todos">
    <h1>ALFI YOVANDANU</h1>
    <h2>Tabel kegiatan</h2>
    <table>
      <thead>
        <tr>
          <th>Kegiatan</th>
          <th>Status</th>
          <th>Tindakan</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="activity in activities" :key="activity.id" :class="{ 'completed': activity.completed }">
          <td>
            <span v-text="activity.name"></span>
          </td>
          <td>
            <span v-text="activity.completed ? 'Selesai' : 'Belum Selesai'"></span>
            <input type="checkbox" v-model="activity.completed">
          </td>
          <td>
            <button @click="cancelActivity(activity.id)">Batalkan</button>
          </td>
        </tr>
      </tbody>
    </table>
    <form @submit.prevent="addActivity">
      <input type="text" placeholder="Masukkan kegiatan baru" v-model="newActivity">
      <button type="submit">Tambahkan</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activities: [
        { id: 1, name: 'Kegiatan 1', completed: false },
        { id: 2, name: 'Kegiatan 2', completed: false }
      ],
      newActivity: ''
    };
  },
  methods: {
    addActivity() {
      if (this.newActivity.trim() !== '') {
        this.activities.push({ id: Date.now(), name: this.newActivity, completed: false });
        this.newActivity = '';
      }
    },
    cancelActivity(id) {
      const index = this.activities.findIndex(activity => activity.id === id);
      if (index !== -1) {
        this.activities.splice(index, 1);
      }
    }
  }
};
</script>


