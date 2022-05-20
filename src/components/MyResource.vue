<template>
  <div id="my-resource">
<!--    <div class="folder-main">-->
<!--    <h2>Mes Dossiers</h2>-->
<!--    <div class="folder-list">-->
<!--      <router-link :key=i v-for="(folder,i) in folders" :to="{name:'folder', params:{name:folder.name}}">-->
<!--        <p><a :class="folder.color">- {{ folder.name }}</a></p>-->
<!--      </router-link>-->
<!--    </div>-->
<!--    </div>-->

<div class="my-resources">
  <article>
    <div class=" items">
      <h2>Mes Dossiers</h2>
      <div class="folder-list">
        <router-link :key=i v-for="(folder,i) in folders" :to="{name:'folder', params:{name:folder.name}}">
          <p><a :class="folder.color">- {{ folder.name }}</a></p>
        </router-link>
      </div>
    </div>
  </article>
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
  text-align: center;
  max-width: 30vw;
}
  #my-resource > div > article:nth-child(1) > div > div{
    width:12vw;
    margin-right:90px;
    text-align: center;
    margin: auto;
  }






.folder-list{
  margin:auto;
  padding-bottom:20px;

}

.my-resources{
  /*display: flex;*/
  /*justify-content: space-evenly;*/
  /*padding-top: 2%;*/
  /*width: 100%;*/
  /*margin:auto;*/
  /*margin: 70px auto;*/

  display:grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap:20px;
  margin-top: 60px;
  width: 100%;

  /*align-items: center;*/

}

.items{
  width:88%;
  border: 1px solid white;
  border-radius:10px;
  margin: -40px 20px;
  padding:1rem;
  max-width: fit-content;
  max-width: 30vw;

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
  border-radius: 10px;



}
.items h2 {
  text-decoration:underline;
}


.folder-main h2{
  color:white;
  text-decoration:underline;
}
.folder-list a:hover{
  color: lightblue;
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