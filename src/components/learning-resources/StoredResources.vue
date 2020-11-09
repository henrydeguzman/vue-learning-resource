<template>
     <ul>
          <learning-resource :link="res.link" :title="res.title" :description="res.description" :key="res.id" v-for="res in resources"></learning-resource> 
     </ul>
</template>

<script>
import LearningResource from './LearningResource.vue';
export default {
     props: ['resources'],
     components: {
          LearningResource
     }
}
</script>