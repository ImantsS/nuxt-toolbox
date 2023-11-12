<template>
  <div v-html="helpContent"></div>
</template>
<script>
import axios from 'axios';

export default {
  data() {
    return {
      helpContent: ''
    };
  },
  mounted() {
    this.fetchHelpContent();
  },
  methods: {
    async fetchHelpContent() {
      try {
        const response = await axios.get('https://cad.onshape.com/help');
        this.helpContent = response.data;
      } catch (error) {
        console.error('Error fetching help content:', error);
      }
    }
  }
};
</script>
<style>
* {
  font-family: 'Helvetica', sans-serif;
}
.intro {
  min-width: 400px;
  padding: 10px 40px;
  width: 60%;
}
</style>
