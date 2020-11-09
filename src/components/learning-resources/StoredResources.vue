<template>
     <ul>
          <learning-resource :link="res.link" :title="res.title" :description="res.description" :key="res.id" v-for="res in resources"></learning-resource> 
     </ul>
</template>

<script>
import LearningResource from './LearningResource.vue';
export default {
     inject: ['resources'],
     components: {
          LearningResource
     }
}
</script>
<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>