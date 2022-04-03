<template>
  <v-app>
    <v-main>
      <FormCreator></FormCreator>      
    </v-main>
  </v-app>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import FormCreator from './components/FormCreator.vue'

export default defineComponent({
  name: 'App',

  components: {
    FormCreator
},

  data () {
    return {
      //
    }
  },
})
</script>
