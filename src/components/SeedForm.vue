<template>
  <div class="seed-form">
    <h3>Add New Seed</h3>
    <form @submit.prevent="saveSeed">
      <div class="form-group">
        <label>Plant Name:</label>
        <input type="text" v-model="seed.plantName" required>
      </div>
      <div class="form-group">
        <label>Seed Count:</label>
        <input type="number" v-model="seed.seedCount" required>
      </div>
      <div class="form-group">
        <label>Shelf Life:</label>
        <input type="date" v-model="seed.shelfLife" required>
      </div>
      <button type="submit">Save Seed</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'SeedForm',
  data() {
    return {
      seed: {
        plantName: '',
        seedCount: 0,
        shelfLife: ''
      }
    }
  },
  methods: {
    async saveSeed() {
      await this.$db.seeds.add(this.seed)
      this.$emit('seed-saved')
      this.seed = {
        plantName: '',
        seedCount: 0,
        shelfLife: ''
      }
    }
  }
}
</script>

<style scoped>
.seed-form {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f5f5f5;
  border-radius: 8px;
}

.form-group {
  margin-bottom: 1rem;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
}

.form-group input {
  width: 100%;
  padding: 0.5rem;
  border: 1px solid #ddd;
  border-radius: 4px;
}

button {
  background-color: #4CAF50;
  color: white;
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}
</style>