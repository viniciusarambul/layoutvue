<template>
  <v-app>
    <v-content>
      <formv3/>
      <templatev3/>
    </v-content>
  </v-app>
</template>

<script>
import templatev3 from './components/templatev3';
import formv3 from './components/formv3';

export default {
  name: 'App',

  components: {
    templatev3,
    formv3,
  }
};
</script>
