<template>
  <div>
    <h2>Seed Management</h2>
    <SeedForm @seed-saved="loadSeeds"/>
    <div class="seed-list">
      <div v-for="seed in seeds" :key="seed.id" class="seed-item">
        <div>{{ seed.plantName }}</div>
        <div>Seed Count: {{ seed.seedCount }}</div>
        <div>Shelf Life: {{ seed.shelfLife }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import SeedForm from './SeedForm.vue'

export default {
  name: 'SeedManager',
  components: { SeedForm },
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

.seed-item div {
  margin: 0.25rem 0;
}
</style>