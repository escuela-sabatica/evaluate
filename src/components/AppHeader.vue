<template>
  <header>
    <h1>EVALÚATE</h1>
    <p>Un antídoto para el estrés, la ansiedad, la depresión y la baja autoestima a través de una relación vibrante con el Creador.</p>
  </header>
</template>

<style scoped>
header {
  background: linear-gradient(rgba(37, 43, 67, 0.8), rgba(40, 46, 71, 0.9)), url('./bg-cover.png');
  background-size: cover;
  background-position: center;
  height: 80vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: white;
  padding: 20px;
}

header h1 {
  font-size: 3.5rem;
  margin-bottom: 1rem;
  border-bottom: 4px solid var(--gold-divine);
  padding-bottom: 10px;
}

header p {
  font-size: 1.2rem;
  max-width: 700px;
  font-style: italic;
}

@media (max-width: 768px) {
  header h1 { font-size: 2.2rem; }
}
</style>
