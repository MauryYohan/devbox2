<template>
  <div class="container">
    <MyFolder :folders="folders" :resources="resources"></MyFolder>
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
    deleteResource: function(_resource){
      this.resources = this.resources.splice(this.resources.indexOf(_resource), 1);
      window.localStorage.setItem("folders", JSON.stringify(this.folders));
    },
    folderItems: function (){
      // if (resource)
    },
    //
  }
}
</script>