<template>
  <div class="app-container">
    <!-- Judul Halaman -->
    <h1 class="title">Account Explorer</h1>
    <SummaryInfo :accounts="accounts" />
    <AccountList :accounts="accounts" />
  </div>
</template>

<script>
import AccountList from './components/AccountList.vue';
import SummaryInfo from './components/SummaryInfo.vue';
import axios from 'axios';

export default {
  name: 'AccountExplorer',
  components: { AccountList, SummaryInfo },
  data() {
    return {
      accounts: [],
    };
  },
  async created() {
    try {
      // Mengambil data akun dari API
      const response = await axios.get('http://localhost:8080/account/list');
      console.log('API Response:', response.data);
      this.accounts = response.data.data;
    } catch (error) {
      console.error('Failed to fetch account data:', error);
    }
  },
};
</script>

<style scoped>
/* Container utama untuk App */
.app-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f8f8f8;
  border-radius: 8px;
}

/* Judul Halaman */
.title {
  font-size: 36px;
  text-align: center;
  margin-bottom: 20px;
  color: #2c3e50;
}

/* Styling untuk komponen Ringkasan (Summary) */
.summary {
  background-color: #ffffff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  margin-bottom: 30px;
}

/* Styling untuk komponen Daftar Akun (Account List) */
.account-list {
  background-color: #ffffff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

/* Setiap item di daftar akun */
.account-item {
  margin-bottom: 15px;
}

/* Desain tombol dan elemen interaktif */
button {
  background-color: #3498db;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #2980b9;
}
</style>
