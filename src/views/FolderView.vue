<template>
  <MyFolder :folders="folders" :resources="resources"></MyFolder>
</template>

<script>
import MyFolder from "@/components/MyFolder";
import HomeView from "@/views/HomeView";

export default {
  name: "FolderView",

  components: {MyFolder},
  data() {
    return {
      resources: HomeView.data().resources,
      folders: HomeView.data().folders,
    }
  }
}
</script>