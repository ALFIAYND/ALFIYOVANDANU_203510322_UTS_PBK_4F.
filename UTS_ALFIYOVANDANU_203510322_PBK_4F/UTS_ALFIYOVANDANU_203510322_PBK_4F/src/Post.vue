<template>
  <div class="Post">
    <h1 class="post-title">Postingan Pengguna</h1>
    <!-- Pilihan untuk memilih pengguna -->
    <select v-model="selectedUser" @change="fetchUserPosts">
      <option v-for="user in users" :key="user.id" :value="user.id">{{ user.name }}</option>
    </select>

    <!-- Menampilkan postingan pengguna yang dipilih -->
    <div v-for="post in userPosts" :key="post.id">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: [],
      selectedUser: null,
      userPosts: []
    };
  },
  methods: {
    async fetchUsers() {
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/users');
        const data = await response.json();
        this.users = data;
      } catch (error) {
        console.error('Gagal mengambil data pengguna:', error);
      }
    },
    async fetchUserPosts() {
      if (!this.selectedUser) return;
      try {
        const response = await fetch(`https://jsonplaceholder.typicode.com/posts?userId=${this.selectedUser}`);
        const data = await response.json();
        this.userPosts = data;
      } catch (error) {
        console.error('Gagal mengambil postingan pengguna:', error);
      }
    }
  },
  created() {
    this.fetchUsers();
  }
};
</script>

<style>
/* Tambahkan gaya Anda di sini */
</style>
