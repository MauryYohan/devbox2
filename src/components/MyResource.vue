<template>
  <div id="my-resource">

    <h2>Ressources Epinglés</h2>
    <div class="resources-list" :key=resource.id v-for="resource in resources">
      <p><a :href="resource.url" target="blank" v-if="resource.pinned">{{resource.name}}</a></p>
    </div>

    <h2>Nos Dossiers</h2>
    <div class="folder-list">
      <router-link :key=i v-for="(folder,i) in folders" :to="{name:'folder', params:{name:folder.name}}">
        <p><a :class="folder.color">{{ folder.name }}</a></p>
      </router-link>
    </div>

    <h2>Ressources non classées</h2>
    <div class="resources-list">
      <ul :key=resource.id v-for="resource in resources">
        <li v-if="resource.folder_id===0"><a :href="resource.url" target="blank">{{resource.name}}</a></li>
      </ul>
    </div>

    <!-- Cette table se met a jour lors d'une insertion via formulaire, les autres non... -->
    <div class="resources-table">
      <table class="table">
        <thead>
          <tr>
            <th scope="col">ID</th>
            <th scope="col">Nom</th>
            <th scope="col">Url</th>
            <th scope="col">Epinglée?</th>
            <th scope="col">Folder</th>
          </tr>
        </thead>
        <tbody>
          <tr :key= resource.id
              v-for="resource in resources"
              class="single-resource">
            <td >{{ resource.id }}</td>
            <td >{{ resource.name }}</td>
            <td><a :href="resource.url">{{resource.url}}</a></td>
            <td>{{ resource.pinned }}</td>
            <td>{{ resource.folder_id }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "MyResource",
  props: { resources: Array, folders: Array, filters: { pinned: true } }
}
</script>

<style scoped>
.folder-list a {
  text-decoration: none;
  cursor:pointer;
  color: grey;
}
.folder-list a.red {
  color: red;
}
.folder-list a.blue {
  color: blue;
}
.folder-list a.yellow {
  color: gold;
}
</style>