<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResMode"
      >Resource List</base-button
    >
    <base-button @click="setSelectedTab('add-resource')" :mode="addNewResMode"
      >Add new Resource
    </base-button>
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import AddResource from './AddResource.vue';
import StoredResources from './StoredResources';

export default {
  components: {
    AddResource,
    StoredResources,
  },
  computed: {
    storedResMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addNewResMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      storedResources: [
        {
          id: 'R-01',
          title: 'Offical Vue.js Guide',
          description: 'Offical Vue.js Guide documentation',
          link: 'https://vuejs.org',
        },
        {
          id: 'R-02',
          title: 'Google',
          description: 'Learn google!',
          link: 'https://google.com',
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResources: this.addResources,
      deleteResource: this.deleteResource,
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResources(resource) {
      this.storedResources.unshift({
        id: new Date().toISOString(),
        title: resource.title,
        description: resource.desc,
        link: resource.link,
      });

      this.selectedTab = 'stored-resources';
    },
    deleteResource(id) {
      const resourceIdx = this.storedResources.findIndex(
        (item) => item.id !== id
      );
      this.storedResources.splice(resourceIdx, 1);
    },
  },
};
</script>