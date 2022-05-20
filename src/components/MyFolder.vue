<template>
<TitlePages />
  <h2>{{$route.params.name}}</h2>
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
import TitlePages from "@/components/TitlePages";
export default {
  name: "MyFolder",
  props: { resources: Array, folders: Array },
components:{TitlePages}
}

</script>

<style scoped>
table{
  margin: auto;
}
/*tr,th,td {*/
/*  display: grid;*/
/*  grid-template-columns: 1fr 1fr 1fr;*/
/*  grid-template-rows: 0.5fr;*/
/*  padding:0.3rem;*/
/*  border:  white;*/
/*}*/
.table tbody tr, .table thead tr{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 0.5fr;
  padding:0.3rem;
  border: 0.2px solid white;
}
tbody{
  margin:auto;
}
th,th,tr,a{
  color:white;
}
.resources-table{
  position: absolute;
  transform: translate(-50%);
  left: 50%;
}
.table th{
  /* margin: auto; */
  /* text-align: center; */
  display: flex;
  justify-content: center;
}
.table tbody tr, .table thead tr{
  margin:auto;
}

h2{
  color:white;
  text-decoration:underline;
  text-decoration:underline;
}
</style>