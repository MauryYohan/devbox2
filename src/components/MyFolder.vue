<template>

  <div class="resources-table" :key=folder.id v-for="folder in folders">
    <div v-if="folder.name===$route.params.name">
      <table class="table">
        <thead>
          <tr>
            <th scope="col">Nom</th>
            <th scope="col">Url</th>
            <th scope="col">Control</th>
          </tr>
        </thead>
        <tbody :key= resource.folder_id v-for="resource in resources">
          <tr v-if="resource.folder_id===folder.id" class="single-resource">
            <td>{{ resource.name }}</td>
            <td><a :href="resource.url">{{resource.url}}</a></td>
            <td><input type="button" value="Supprimer" @click="folders.deleteResource(resource)" class="product-delete-cart"></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>

</template>

<script>
export default {
  name: "MyFolder",
  props: { resources: Array, folders: Array },

}

</script>

<style scoped>

</style>