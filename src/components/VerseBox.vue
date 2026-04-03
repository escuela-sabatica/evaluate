<template>
  <div class="verse-box">
    <slot />
  </div>
</template>

<style scoped>
.verse-box {
  background: linear-gradient(rgba(37, 43, 67, 0.8), rgb(40, 46, 71)), url("/bg-cover.png");
  background-size: cover;
  background-position: center;
  color: var(--gold-divine);
  padding: 40px;
  text-align: center;
  font-size: 1.5rem;
  font-weight: bold;
  border-radius: 15px;
  margin: 40px 0;
  box-shadow: 0 4px 17px rgba(0, 0, 0, 0.05);
}
</style>
