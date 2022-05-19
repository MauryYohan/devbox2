<template>
  <div id="my-resource">
    <div class="folder-main">
    <h2>Mes Dossiers</h2>
    <div class="folder-list">
      <router-link :key=i v-for="(folder,i) in folders" :to="{name:'folder', params:{name:folder.name}}">
        <p><a :class="folder.color">- {{ folder.name }}</a></p>
      </router-link>
    </div>
    </div>

<div class="my-resources">
  <article class="items hero">
    <h2>Ressources Epinglées</h2>
    <div class="resources-list" :key=resource.id v-for="resource in resources">
      <p><a :href="resource.url" target="blank" v-if="resource.pinned">{{resource.name}}</a></p>
    </div>
  </article>

  <article class="items">
    <h2>Ressources non classées</h2>
    <div class="resources-list">
      <ul :key=resource.id v-for="resource in resources">
        <li v-if="resource.folder_id===0"><a :href="resource.url" target="blank">{{resource.name}}</a></li>
      </ul>
    </div>
  </article>
</div>
    <!-- Cette table se met a jour lors d'une insertion via formulaire, les autres non... -->

<!--    -->
<!--    <div class="resources-table">-->
<!--      <table class="table">-->
<!--        <thead>-->
<!--          <tr>-->
<!--            <th scope="col">ID</th>-->
<!--            <th scope="col">Nom</th>-->
<!--            <th scope="col">Url</th>-->
<!--            <th scope="col">Epinglée?</th>-->
<!--            <th scope="col">Folder</th>-->
<!--          </tr>-->
<!--        </thead>-->
<!--        <tbody>-->
<!--          <tr :key= resource.id-->
<!--              v-for="resource in resources"-->
<!--              class="single-resource">-->
<!--            <td >{{ resource.id }}</td>-->
<!--            <td >{{ resource.name }}</td>-->
<!--            <td><a :href="resource.url">{{resource.url}}</a></td>-->
<!--            <td>{{ resource.pinned }}</td>-->
<!--            <td>{{ resource.folder_id }}</td>-->
<!--          </tr>-->
<!--        </tbody>-->
<!--      </table>-->
<!--    </div>-->
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
.folder-main{
  display: flex;
  justify-content: start;
  flex-direction: column;
  width: 20%;

background:black;
  border-radius:40px;
  margin-top: -80px;

  position: absolute;
  top: 370px;

}
.folder-list a {
  text-align: start;

}
.folder-list{
  margin:auto;
  padding-bottom:20px;
}

.my-resources{
  display: flex;
  justify-content: center;
  padding-top: 2%;
  width: 50%;
  margin:auto;
  /*margin-top: -60px;*/
  margin: 160px auto;
  /* margin-top: -60px; */
}

.items{
  width: 50%;
  border: 1px solid white;
  margin: -40px 20px;
  padding:1rem;

}

.items li{
  list-style:none;
  color:white;
}

.items div a{
  color: white;
  text-decoration:none;
}
.product{
  color: white;
  position:absolute;
  right:0;
}
#addResourceForm > div{
  position:absolute ;
  right:0;

}

.hero{
  background:darkgoldenrod;
}
.items h2 {
  text-decoration:underline;
}
.hero{
  border-radius: 50px;
}

.folder-main h2{
  color:white;
  text-decoration:underline;
}
.items h2{
  color:white;
}

.hero{
  border: black;
}
.items a:hover{
  color: lightblue;
  text-decoration:underline;
}
</style>