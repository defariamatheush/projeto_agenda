<template>
  <v-container>
    <Formulario />
  </v-container>
</template>

<script>
import { defineComponent } from 'vue';
import Formulario from '@/components/Formulario.vue';
// Components


export default defineComponent({
  name: 'HomeView',

  components: {
    Formulario,
  },
});
</script>
