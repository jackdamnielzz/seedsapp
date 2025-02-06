<template>
  <div>
    <h2>Seed Management</h2>
    <div class="seed-list">
      <div v-for="seed in seeds" :key="seed.id" class="seed-item">
        <div>{{ seed.plantName }}</div>
        <div>Seed Count: {{ seed.seedCount }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SeedManager',
  data() {
    return {
      seeds: []
    }
  },
  mounted() {
    this.loadSeeds()
  },
  methods: {
    async loadSeeds() {
      const seeds = await this.$db.seeds.toArray()
      this.seeds = seeds
    }
  }
}
</script>

<style scoped>
.seed-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-top: 1rem;
}

.seed-item {
  padding: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>