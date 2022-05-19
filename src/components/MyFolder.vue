<template>

  <div id="my-folder" :key=folder.id v-for="folder in folders">
    <div v-if="folder.name===$route.params.name">
      <h3 class="folder-name">{{folder.name}}</h3>
      <div id="my-resource" :key="resource.id" v-for="resource in resources">
          <table class="resource-table" v-if="resource.folder_id===folder.id">
            <thead>
            <tr>
              <th scope="col">Nom</th>
              <th scope="col">Url</th>
            </tr>
            </thead>
            <tbody>
            <tr :key= folder.id>
                  <td >{{ resource.name }}</td>
                  <td :href="resource.url">{{resource.url}}</td>
            </tr>
            </tbody>
          </table>
<!--          <a :href="resource.url" target="_blank">{{resource.name}}</a>-->
      </div>
    </div>
  </div>
<!--    _______________________-->
<!--    <div class="resources-table">-->
<!--      <table class="table">-->
<!--        <thead>-->
<!--        <tr>-->
<!--          <th scope="col">Nom</th>-->
<!--          <th scope="col">Url</th>-->
<!--        </tr>-->
<!--        </thead>-->
<!--        <tbody>-->
<!--          <tr :key= folder.id-->
<!--              v-for="folder in folders"-->
<!--              class="single-folder">-->
<!--            <div v-if="folder.name===$route.params.name"></div>-->
<!--&lt;!&ndash;            <td >{{ folder.id }}</td>&ndash;&gt;-->
<!--            <div id="my-resource" :key="resource.id" v-for="resource in resources">-->
<!--              <article v-if="resource.folder_id===folder.id">-->
<!--            <p >{{ resource.name }}</p>-->
<!--            <a :href="resource.url">{{resource.url}}</a>-->
<!--              </article>-->
<!--            </div>-->
<!--          </tr>-->

<!--        </tbody>-->

<!--      </table>-->
<!--    </div>-->


</template>

<script>
export default { name: "MyFolder", props: { resources: Array, folders: Array } }
</script>

<style scoped>

</style>