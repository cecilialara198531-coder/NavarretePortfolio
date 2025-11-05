<script setup>
import { computed } from 'vue'

const props = defineProps(['persona'])
const metasDylan = [
  {
    titulo: 'Jugar muchos juegos en Stream',
    descripcion: 'Tener una biblioteca variada de juegos para entretenerme',
  },
  {
    titulo: 'Terminar mis estudios de Informática',
    descripcion: 'Grafuarme del colegio con buenos promedios',
  },
  {
    titulo: 'Trabajar en Google como programador',
    descripcion: 'Lo que más me apasiona y mi modelo a seguir es trabajar en Google como programador'
  },
  {
    titulo: 'Aprender nuevas tecnologías',
    descripcion: 'Mantenerme actualizado con las últimas tendencias tech'
  }
]
const metasLesly = [
  {
    titulo: 'Crecer como persona ',
    descripcion: 'Desarrollar habilidades sociales y emocionales',
  },
  {
    titulo: 'Ganar seguidores en redes sociales',
    descripcion: 'Construir una comunidad en línea sólida',
  },
  {
    titulo: 'Terminar mis estudios ',
    descripcion: 'Graduarme y culminar mi formación académica'
  },
  {
    titulo: 'Trabajar en mis habilidades ',
    descripcion: 'Mejorar mis competencias técnicas y profesionales'
  }
]
const metasActivas = computed(() => {
  return props.persona === 'Dylan' ? metasDylan : metasLesly
})
</script>

<template>
  <section class="metas">
    <h2 :class="persona === 'Dylan' ? 'titulo-dylan' : 'titulo-lesly'">🎯 Mis Metas</h2>
    <div class="metas-grid">
      <div 
        v-for="(meta, index) in metasActivas" 
        :key="index"
        :class="['meta-card', persona === 'Dylan' ? 'meta-card-dylan' : 'meta-card-lesly']"
      >
        <div class="meta-icono">{{ meta.icono }}</div>
        <h3>{{ meta.titulo }}</h3>
        <p>{{ meta.descripcion }}</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.metas {
  padding: 2.5rem;
  margin-bottom: 2rem;
}

.metas h2 {
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

.metas-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
}

.meta-card {
  background: white;
  padding: 2rem;
  border-radius: 15px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s, box-shadow 0.3s;
  text-align: center;
}

.meta-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
}

.meta-card-dylan {
  border-top: 4px solid #ff6b35;
}

.meta-card-lesly {
  border-top: 4px solid #9d50bb;
}

.meta-icono {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.meta-card h3 {
  font-size: 1.3rem;
  margin-bottom: 0.8rem;
  color: #333;
}

.meta-card-dylan h3 {
  color: #ff6b35;
}

.meta-card-lesly h3 {
  color: #9d50bb;
}

.meta-card p {
  color: #666;
  line-height: 1.6;
}
</style>