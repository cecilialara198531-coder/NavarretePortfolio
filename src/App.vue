<script setup>
import { ref } from 'vue'
import Encabezado from './components/Encabezado.vue'
import Biografia from './components/Biografia.vue'
import Metas from './components/Metas.vue'
import Redes from './components/Redes.vue'
const perfilActivo = ref(null)
const seleccionarPerfil = (nombre) => {
  perfilActivo.value = nombre
}
const volverInicio = () => {
  perfilActivo.value = null
}
</script>

<template>
  <div class="app-container">
    <div v-if="!perfilActivo" class="selector-perfiles">
      <h1>Mi Portafolio con Astro</h1>
      <p>Selecciona un perfil para ver:</p>
      <div class="botones-perfiles">
        <button @click="seleccionarPerfil('Dylan')" class="btn-dylan">
          Dylan Navarrete
        </button>
        <button @click="seleccionarPerfil('Lesly')" class="btn-lesly">
          Lesly Correa
        </button>
      </div>
    </div>
    <div v-else :class="['perfil-container', perfilActivo === 'Dylan' ? 'tema-dylan' : 'tema-lesly']">
      <button @click="volverInicio" class="btn-volver">← Volver</button>
      
      <Encabezado :persona="perfilActivo" />
      <Biografia :persona="perfilActivo" />
      <Metas :persona="perfilActivo" />
      <Redes :persona="perfilActivo" />
    </div>
  </div>
</template>

<style scoped>
.app-container {
  min-height: 100vh;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
.selector-perfiles {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
}

.selector-perfiles h1 {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.selector-perfiles p {
  font-size: 1.2rem;
  margin-bottom: 2rem;
}

.botones-perfiles {
  display: flex;
  gap: 2rem;
  flex-wrap: wrap;
  justify-content: center;
}

.botones-perfiles button {
  padding: 1.5rem 3rem;
  font-size: 1.3rem;
  font-weight: bold;
  border: none;
  border-radius: 15px;
  cursor: pointer;
  transition: transform 0.3s, box-shadow 0.3s;
  color: white;
}

.btn-dylan {
  background: linear-gradient(135deg, #ff6b35 0%, #f7931e 100%);
}

.btn-lesly {
  background: linear-gradient(135deg, #9d50bb 0%, #6e48aa 100%);
}

.botones-perfiles button:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
}

/* Contenedor del perfil */
.perfil-container {
  min-height: 100vh;
  padding: 2rem;
}

.tema-dylan {
  background: linear-gradient(to bottom, #fff5f0 0%, #ffe8d6 100%);
}

.tema-lesly {
  background: linear-gradient(to bottom, #f5f0ff 0%, #e8d6ff 100%);
}

.btn-volver {
  padding: 0.8rem 1.5rem;
  font-size: 1rem;
  font-weight: bold;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  margin-bottom: 2rem;
  background: rgba(0, 0, 0, 0.1);
  color: #333;
  transition: background 0.3s;
}

.btn-volver:hover {
  background: rgba(0, 0, 0, 0.2);
}
</style>
