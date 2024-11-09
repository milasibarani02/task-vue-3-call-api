<template>
  <div class="account-list-container">
    <h2 class="account-list-title">Account List</h2>
    <div v-if="accounts.length === 0" class="no-accounts-message">
      No accounts available.
    </div>
    <div v-else class="account-card-wrapper">
      <div
        v-for="account in accounts"
        :key="account.account_id"
        class="account-card"
      >
        <div class="account-details">
          <h3 class="account-name">{{ account.name }}</h3>
          <p class="account-id">Account ID: {{ account.account_id }}</p>
          <p class="account-balance">Balance: Rp {{ account.balance.toLocaleString() }}</p>
        </div>
        <div class="account-actions">
          <button @click="viewDetails(account.account_id)" class="btn btn-view">View</button>
          <button @click="editAccount(account.account_id)" class="btn btn-edit">Edit</button>
          <button @click="deleteAccount(account.account_id)" class="btn btn-delete">Delete</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AccountList',
  props: {
    accounts: Array,
  },
  methods: {
    viewDetails(accountId) {
      // Handle view account details
      console.log('View account with ID:', accountId);
    },
    editAccount(accountId) {
      // Handle editing account
      console.log('Edit account with ID:', accountId);
    },
    deleteAccount(accountId) {
      // Handle account deletion
      console.log('Delete account with ID:', accountId);
    },
  },
};
</script>

<style scoped>
.account-list-container {
  padding: 20px;
  max-width: 900px;
  margin: auto;
}

.account-list-title {
  font-size: 1.8em;
  font-weight: bold;
  text-align: center;
  margin-bottom: 20px;
}

.no-accounts-message {
  text-align: center;
  color: #888;
  font-size: 1.2em;
}

.account-card-wrapper {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 20px;
  margin-top: 20px;
}

.account-card {
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
}

.account-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
}

.account-details {
  margin-bottom: 15px;
}

.account-name {
  font-size: 1.4em;
  font-weight: bold;
  color: #333;
}

.account-id,
.account-balance {
  font-size: 1.1em;
  color: #555;
}

.account-actions {
  display: flex;
  justify-content: space-between;
}

.btn {
  padding: 8px 15px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1em;
}

.btn-view {
  background-color: #4CAF50;
  color: #fff;
}

.btn-edit {
  background-color: #FFC107;
  color: #fff;
}

.btn-delete {
  background-color: #f44336;
  color: #fff;
}

.btn:hover {
  opacity: 0.8;
}
</style>
