<template>
  <div class="section">
    <div class="quiz-container">

      <!-- PANTALLA DEL QUIZ -->
      <div v-if="!quizFinished" id="quiz-screen">
        <div class="stats-bar">
          <span>Pregunta: <strong>{{ currentQ + 1 }} / {{ quizData.length }}</strong></span>
          <span>Aciertos: <strong>{{ score }}</strong></span>
        </div>

        <div class="progress-bar">
          <div class="progress-fill" :style="{ width: progressPercent + '%' }"></div>
        </div>

        <div class="question-box">
          <h3>{{ current.q }}</h3>

          <button
            v-for="(opt, i) in current.options"
            :key="i"
            class="option-btn"
            :class="getOptionClass(i)"
            :disabled="answered"
            @click="checkAnswer(i)"
          >
            {{ opt }}
          </button>
        </div>

        <transition name="fade">
          <div
            v-if="answered"
            class="feedback-area"
            :class="lastCorrect ? 'feedback-correct' : 'feedback-wrong'"
          >
            <strong>{{ lastCorrect ? '¡Correcto!' : 'Respuesta Incorrecta' }}</strong>
            <p>{{ current.desc }}</p>
            <button class="btn-next" @click="nextQuestion">Siguiente</button>
          </div>
        </transition>
      </div>

      <!-- PANTALLA DE RESULTADOS -->
      <div v-else class="result-screen">
        <h2>Diagnóstico Final Completado</h2>
        <div class="score-circle">{{ score }}/{{ quizData.length }}</div>
        <p>{{ finalMessage }}</p>
        <button class="btn-next" @click="restartQuiz">Reiniciar</button>
      </div>

    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { quizData } from '../data/quizData.js'

// ── State ──────────────────────────────────────────────
const currentQ   = ref(0)
const score      = ref(0)
const answered   = ref(false)
const lastCorrect = ref(false)
const selectedIndex = ref(null)
const quizFinished  = ref(false)

// ── Computed ───────────────────────────────────────────
const current = computed(() => quizData[currentQ.value])

const progressPercent = computed(() =>
  (currentQ.value / quizData.length) * 100
)

const finalMessage = computed(() => {
  const pct = score.value / quizData.length
  if (pct >= 0.8) return '¡Excelente! Tienes un conocimiento profundo.'
  if (pct >= 0.5) return 'Buen progreso. Sigue fortaleciendo tu conexión.'
  return 'Es momento de volver a las fuentes.'
})

// ── Methods ────────────────────────────────────────────
function getOptionClass(i) {
  if (!answered.value) return ''
  if (i === current.value.correct) return 'correct'
  if (i === selectedIndex.value)   return 'wrong'
  return ''
}

function checkAnswer(index) {
  if (answered.value) return
  answered.value   = true
  selectedIndex.value = index
  lastCorrect.value   = index === current.value.correct
  if (lastCorrect.value) score.value++
}

function nextQuestion() {
  currentQ.value++
  answered.value = false
  selectedIndex.value = null
  if (currentQ.value >= quizData.length) quizFinished.value = true
}

function restartQuiz() {
  currentQ.value   = 0
  score.value      = 0
  answered.value   = false
  selectedIndex.value = null
  quizFinished.value  = false
}
</script>

<style scoped>
.quiz-container {
  background: white;
  padding: 40px;
  border-radius: 15px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  border-left: 5px solid var(--gold-divine);
}

.stats-bar {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
  font-weight: bold;
  color: var(--primary-navy);
}

.progress-bar {
  width: 100%;
  height: 10px;
  background: #eee;
  border-radius: 5px;
  margin-bottom: 30px;
}

.progress-fill {
  height: 100%;
  background: var(--gold-divine);
  transition: width 0.4s;
}

.question-box h3 {
  margin-bottom: 20px;
  color: var(--primary-navy);
}

.option-btn {
  display: block;
  width: 100%;
  padding: 15px;
  margin: 10px 0;
  background: var(--white-pure);
  border: 1px solid #ddd;
  border-radius: 8px;
  cursor: pointer;
  text-align: left;
  font-size: 1rem;
  transition: 0.2s;
}

.option-btn:hover:not([disabled]) {
  border-color: var(--gold-divine);
  background: #fdfaf0;
}

.option-btn.correct { background: var(--correct-green) !important; color: white; border-color: var(--correct-green); }
.option-btn.wrong   { background: var(--accent-red)    !important; color: white; border-color: var(--accent-red);   }

.feedback-area {
  margin-top: 20px;
  padding: 20px;
  border-radius: 8px;
}

.feedback-correct { background: #e8f5e9; border-left: 5px solid var(--correct-green); }
.feedback-wrong   { background: #ffebee; border-left: 5px solid var(--accent-red);   }

.btn-next {
  background: var(--primary-navy);
  color: white;
  padding: 12px 30px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 20px;
  transition: all 0.3s;
}

.btn-next:hover { background: var(--gold-divine); }

.result-screen {
  text-align: center;
}

.score-circle {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  border: 8px solid var(--gold-divine);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2.5rem;
  font-weight: bold;
  margin: 30px auto;
  color: var(--primary-navy);
}
/* Transition Vue */
.fade-enter-active { animation: fadeIn 0.5s; }
@keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
@media (max-width: 768px) {
  .quiz-container{
    padding: 30px 20px;
  }
}  
</style>
