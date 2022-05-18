<template>

  <div id="my-folder" :key=folder.id v-for="folder in folders">
    <div v-if="folder.name===$route.params.name">
      <h3 class="folder-name">{{folder.name}}</h3>
      <div id="my-resource" :key="resource.id" v-for="resource in resources">
        <p v-if="resource.folder_id===folder.id">
          <a :href="resource.url" target="_blank">{{resource.name}}</a>
        </p>
      </div>
    </div>
  </div>

</template>

<script>
export default { name: "MyFolder", props: { resources: Array, folders: Array } }
</script>

<style scoped>

</style>