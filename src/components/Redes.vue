<script setup>
import { computed } from 'vue'

const props = defineProps(['persona'])
const redesDylan = [
  {
    nombre: 'GitHub',
    icono: '💻',
    url: 'https://github.com/tu-usuario-dylan',
    usuario: '@dylannavarrete'
  },
  {
    nombre: 'LinkedIn',
    icono: '💼',
    url: 'https://linkedin.com/in/tu-perfil-dylan',
    usuario: 'Dylan Navarrete'
  },
  {
    nombre: 'Instagram',
    icono: '📸',
    url: 'https://instagram.com/tu-usuario-dylan', 
    usuario: '@dylan_dev'
  },
  {
    nombre: 'Email',
    icono: '📧',
    url: 'mailto:dylan@ejemplo.com',
    usuario: 'dylan@ejemplo.com'
  }
]
const redesLesly = [
  {
    nombre: 'GitHub',
    icono: '💻',
    url: 'https://github.com/tu-usuario-lesly', 
    usuario: '@leslycorreo'
  },
  {
    nombre: 'LinkedIn',
    icono: '💼',
    url: 'https://linkedin.com/in/tu-perfil-lesly', 
    usuario: 'Lesly Correo'
  },
  {
    nombre: 'Instagram',
    icono: '📸',
    url: 'https://instagram.com/tu-usuario-lesly', 
    usuario: '@lesly_dev'
  },
  {
    nombre: 'Email',
    icono: '📧',
    url: 'mailto:lesly@ejemplo.com', 
    usuario: 'lesly@ejemplo.com'
  }
]

const redesActivas = computed(() => {
  return props.persona === 'Dylan' ? redesDylan : redesLesly
})
</script>

<template>
  <section class="redes">
    <h2 :class="persona === 'Dylan' ? 'titulo-dylan' : 'titulo-lesly'">🌐 Mis Redes Sociales</h2>
    <div class="redes-grid">
      <a 
        v-for="(red, index) in redesActivas" 
        :key="index"
        :href="red.url"
        target="_blank"
        rel="noopener noreferrer"
        :class="['red-card', persona === 'Dylan' ? 'red-card-dylan' : 'red-card-lesly']"
      >
        <div class="red-icono">{{ red.icono }}</div>
        <h3>{{ red.nombre }}</h3>
        <p>{{ red.usuario }}</p>
      </a>
    </div>
  </section>
</template>

<style scoped>
.redes {
  padding: 2.5rem;
  margin-bottom: 2rem;
}

.redes h2 {
  font-size: 2rem;
  margin-bottom: 2rem;
  text-align: center;
}

.titulo-dylan {
  color: #ff6b35;
}

.titulo-lesly {
  color: #9d50bb;
}

.redes-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1.5rem;
}

.red-card {
  background: white;
  padding: 2rem;
  border-radius: 15px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s, box-shadow 0.3s;
  text-align: center;
  text-decoration: none;
  color: inherit;
  display: block;
}

.red-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 35px rgba(0, 0, 0, 0.2);
}

.red-card-dylan:hover {
  border-color: #ff6b35;
}

.red-card-lesly:hover {
  border-color: #9d50bb;
}

.red-icono {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.red-card h3 {
  font-size: 1.3rem;
  margin-bottom: 0.5rem;
  color: #333;
}

.red-card-dylan h3 {
  color: #ff6b35;
}

.red-card-lesly h3 {
  color: #9d50bb;
}

.red-card p {
  color: #666;
  font-size: 0.9rem;
}
</style>