<script setup>
import { computed } from 'vue'

const props = defineProps(['persona'])
const datosDylan = {
  nombre: 'Dylan Navarrete',
  titulo: 'Estudiante de Informática',
  foto: 'public/1.png',
}
const datosLesly = {
  nombre: 'Lesly Correa',
  titulo: 'Estudiante de la Informática ',
  foto: 'public/2.png',
}
const datosActivos = computed(() => {
  return props.persona === 'Dylan' ? datosDylan : datosLesly
})
</script>

<template>
  <header :class="['encabezado', persona === 'Dylan' ? 'encabezado-dylan' : 'encabezado-lesly']">
    <div class="foto-container">
      <img :src="datosActivos.foto" :alt="datosActivos.nombre" class="foto-perfil">
    </div>
    <div class="info-container">
      <h1>{{ datosActivos.nombre }}</h1>
      <h2>{{ datosActivos.titulo }}</h2>
      <p>{{ datosActivos.descripcion }}</p>
    </div>
  </header>
</template>

<style scoped>
.encabezado {
  display: flex;
  align-items: center;
  gap: 2rem;
  padding: 3rem;
  border-radius: 20px;
  margin-bottom: 2rem;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.1);
  flex-wrap: wrap;
  justify-content: center;
}

.encabezado-dylan {
  background: linear-gradient(135deg, #ff6b35 0%, #f7931e 100%);
  color: white;
}

.encabezado-lesly {
  background: linear-gradient(135deg, #9d50bb 0%, #6e48aa 100%);
  color: white;
}

.foto-container {
  flex-shrink: 0;
}

.foto-perfil {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  border: 5px solid white;
  object-fit: cover;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
}

.info-container h1 {
  font-size: 2.5rem;
  margin-bottom: 0.5rem;
}

.info-container h2 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  opacity: 0.9;
}

.info-container p {
  font-size: 1.1rem;
  opacity: 0.9;
}

@media (max-width: 768px) {
  .encabezado {
    flex-direction: column;
    text-align: center;
  }
}
</style>