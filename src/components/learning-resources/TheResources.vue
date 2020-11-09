<template>
     <base-card>
          <base-button @click="setSelectedTab('stored-resources')" 
               :mode="storedResButtonMode"
               >Stored Resources</base-button>
          <base-button :mode="addResButtonMode" @click="setSelectedTab('add-resource')">Add Resource</base-button>
     </base-card>
     <keep-alive>
          <component :is="selectedTab"></component>
     </keep-alive>     
</template>

<script>
import AddResource from './AddResource.vue'
import StoredResources from './StoredResources.vue'

export default {
     components: {
          AddResource,
          StoredResources
     },
     computed: {
          storedResButtonMode () {
               return this.selectedTab === 'stored-resources' ? null : 'flat'
          },
          addResButtonMode () {
               return this.selectedTab === 'add-resource' ? null : 'flat'
          }
     },
     data () {
          return {
               selectedTab: 'stored-resources',
               storedResources: [
                    { id: 'official-guide', title: 'Official Guide', description: 'The Official Vue.js Documentation', link: 'https://vuejs.org' },
                    { id: 'google', title: 'Google', description: 'Learn to google...', link: 'https://google.org' }
               ]
          }
     },
     provide () {
          return {
               resources: this.storedResources,
               addResource: this.addResource
          }
     },
     methods: {
          setSelectedTab (tab) {
               this.selectedTab = tab
          },
          addResource (title, description, url) {

               const newResource = {
                    id: new Date().toISOString(),
                    title,
                    description,
                    link: url
               }
               console.log(newResource)
               this.storedResources.unshift(newResource);
               this.selectedTab = 'stored-resources'
          }
     }
}
</script>