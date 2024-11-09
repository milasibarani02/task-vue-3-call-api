<template>
  <div class="summary-container">
    <h2 class="summary-title">Account Summary</h2>
    <div class="summary-card">
      <p class="summary-item">
        <span class="summary-label">Total Data Account:</span>
        <span class="summary-value">{{ totalAccounts }}</span>
      </p>
      <p class="summary-item">
        <span class="summary-label">Total Balance:</span>
        <span class="summary-value">Rp {{ totalBalance.toLocaleString() }}</span>
      </p>
      <p class="summary-item">
        <span class="summary-label">Average Balance:</span>
        <span class="summary-value">Rp {{ averageBalance.toLocaleString() }}</span>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SummaryInfo',
  props: {
    accounts: Array,
  },
  computed: {
    totalAccounts() {
      return this.accounts.length;
    },
    totalBalance() {
      return this.accounts.reduce((sum, account) => sum + account.balance, 0);
    },
    averageBalance() {
      return this.totalBalance / this.totalAccounts || 0;
    },
  },
};
</script>

<style scoped>
.summary-container {
  margin: 20px;
  padding: 20px;
  background-color: #f4f7fc;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  max-width: 400px;
  margin-left: auto;
  margin-right: auto;
}

.summary-title {
  font-size: 1.8em;
  font-weight: bold;
  color: #333;
  text-align: center;
  margin-bottom: 20px;
}

.summary-card {
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.summary-item {
  font-size: 1.2em;
  margin: 10px 0;
}

.summary-label {
  font-weight: 600;
  color: #555;
}

.summary-value {
  font-weight: 600;
  color: #333;
  margin-left: 10px;
}

@media (max-width: 600px) {
  .summary-container {
    max-width: 100%;
    padding: 15px;
  }

  .summary-title {
    font-size: 1.5em;
  }

  .summary-item {
    font-size: 1.1em;
  }
}
</style>
