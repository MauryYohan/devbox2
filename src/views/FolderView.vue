<template>
  <div>
  <MyFolder :folders="folders" :resources="resources"></MyFolder>
  <div :key="folder.id" v-for="folder in folders">
<!--    <article v-if="folder.id===folder.name">-->
<!--      {{folder.name}}-->
<!--    </article>-->

    <div :key="i" v-for="(resource,i) in resources" :to="{name:'folder', params:{name:folder.name}}">
      <article v-if="resource.folder_id === resource.id">
        {{resource.name}}
      </article>
    </div>
</div>
  </div>
</template>

<script>
import MyFolder from "@/components/MyFolder";

export default {
  name: "FolderView",

  components: {MyFolder},
  data() {
    return {
      resources: [],
      folders: [],
    }
  },
  mounted() {
    this.resources = localStorage.getItem('resources') ? JSON.parse(localStorage.getItem('resources')) : this.resources;
    this.folders = localStorage.getItem('folders') ? JSON.parse(localStorage.getItem('folders')) : this.folders;
  },
  methods: {
    folderItems: function (){
      // if (resource)
    }
  }
}
</script>