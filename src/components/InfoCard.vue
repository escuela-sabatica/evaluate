<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <p>{{ text }}</p>
  </div>
</template>

<script setup>
defineProps({
  title: { type: String, required: true },
  text:  { type: String, required: true }
})
</script>
<style scoped>
.card {
  background: white;
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
  transition: transform 0.3s;
  border-left: 5px solid var(--gold-divine);
}
.card:hover { transform: translateY(-8px); }
.card h3 {
  color: var(--primary-navy);
  margin-bottom: 16px;
}
@media (max-width: 768px) {
  .card{
    padding: 30px 20px;
  }
}    
</style>
