<template>
  <AppHeader />

  <!-- Sección 1: El Diagnóstico -->
  <section class="section">
    <h2>El Diagnóstico del Testigo Fiel</h2>
    <p class="section-intro">
      Nuestra condición espiritual no puede mejorar sin una evaluación honesta de nuestra realidad
      y la escucha activa de la solución que Jesús ofrece.
    </p>

    <div class="grid">
      <InfoCard
        title="La Disonancia Cognitiva"
        text="A menudo pensamos que somos ricos y autosuficientes, pero el Testigo Fiel nos revela que somos «infelices, miserables, pobres, ciegos y desnudos»."
      />
      <InfoCard
        title="El Estado de Tibieza"
        text="La tibieza espiritual provoca náuseas en el sistema divino. Es mejor una definición fría o caliente que una mediocridad intermitente."
      />
      <InfoCard
        title="La Oferta de Intercambio"
        text="Jesús ofrece su oro refinado, vestiduras blancas y colirio para restaurar nuestra visión y cubrir nuestra desnudez espiritual."
      />
    </div>

    <VerseBox>
      "Como el Padre me amó, también yo los he amado; permaneced en mi amor"
      <br />
      <span class="verse-ref">— Juan 15:9</span>
    </VerseBox>
  </section>

  <!-- Sección 2: Permanecer en la Vid -->
  <section class="section section-white">
    <h2>Permanecer en la Vid</h2>
    <div class="grid">
      <InfoCard
        title="La Savia del Sistema"
        text="El Espíritu Santo actúa como la savia que fluye. Sin pedir diariamente esta presencia, la rama se deshidrata y deja de dar fruto."
      />
      <InfoCard
        title="La Puerta Abierta"
        text="Él llama pacientemente. No irrumpe por la fuerza. La cena representa un diálogo estrecho y una relación duradera que lo cambia todo."
      />
    </div>
  </section>

  <!-- Sección 3: Quiz -->
  <QuizSection />

  <AppFooter />
</template>

<script setup>
import AppHeader    from './components/AppHeader.vue'
import AppFooter    from './components/AppFooter.vue'
import InfoCard     from './components/InfoCard.vue'
import VerseBox     from './components/VerseBox.vue'
import QuizSection  from './components/QuizSection.vue'
</script>
<style>
.section-intro {
  text-align: center;
  max-width: 800px;
  margin: auto;
}
.section-white {
  background: #fff;
}
.verse-ref {
  font-size: 1rem;
  color: white;
}
@media (max-width: 768px) {
 h2{font-size: 2rem;}
}  
</style>
