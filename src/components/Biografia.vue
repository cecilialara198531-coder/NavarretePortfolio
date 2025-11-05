<script setup>
import { computed } from 'vue'

const props = defineProps(['persona'])
const biografiaDylan = `
Soy Dylan Navarrete, un estudiante apasionado por la tecnología y el desarrollo web. 
Me encanta aprender jugar videojuegos y las computadoras. Actualmente estoy 
estudiando programación y desarrollo de aplicaciones web.

En mi tiempo libre disfruto de la música, los videojuegos y pasar tiempo con mis amigos. 
Mi objetivo es convertirme en un streamer, o tal vez trabajar en una empresa de tecnología.
`
const biografiaLesly = `
Hola, soy Lesly Correa, estudiante de Segundo Informática.

Disfruto de la música y las redes sociales. Me interesa la informática y las líneas de código.
Mi objetivo es terminar mis estudios en la Unidad Eduactiva Alessandro Volta.
`
const biografiaActiva = computed(() => {
  return props.persona === 'Dylan' ? biografiaDylan : biografiaLesly
})
</script>

<template>
  <section :class="['biografia', persona === 'Dylan' ? 'biografia-dylan' : 'biografia-lesly']">
    <h2>📖 Sobre Mí</h2>
    <div class="biografia-contenido">
      <p>{{ biografiaActiva }}</p>
    </div>
  </section>
</template>

<style scoped>
.biografia {
  padding: 2.5rem;
  border-radius: 20px;
  margin-bottom: 2rem;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
  background: white;
}

.biografia-dylan {
  border-left: 5px solid #ff6b35;
}

.biografia-lesly {
  border-left: 5px solid #9d50bb;
}

.biografia h2 {
  font-size: 2rem;
  margin-bottom: 1.5rem;
  color: #333;
}

.biografia-dylan h2 {
  color: #ff6b35;
}

.biografia-lesly h2 {
  color: #9d50bb;
}

.biografia-contenido {
  line-height: 1.8;
  font-size: 1.1rem;
  color: #555;
}

.biografia-contenido p {
  white-space: pre-line;
  margin: 0;
}
</style>