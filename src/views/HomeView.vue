<template>
 <div class="container">
   <!--  LETTERS-->

   <ul class="my-title-main">
     <li>
       <input type="checkbox" />
       <div class="letter">D</div>
     </li>
     <li>
       <input type="checkbox" />
       <div class="letter">E</div>
     </li>
     <li>
       <input type="checkbox" />
       <div class="letter">V</div>
     </li>
     <li>
       <input type="checkbox" />
       <div class="letter">B</div>
     </li>
     <li>
       <input type="checkbox" />
       <div class="letter">O</div>
     </li>
     <li>
       <input type="checkbox" />
       <div class="letter">X</div>
     </li>
     <!--    <li>-->
     <!--      <input type="checkbox" />-->
     <!--      <div class="letter">M</div>-->
     <!--    </li>-->
   </ul>
   <!--  LETTERS-->


  <form>
        <img alt="Vue logo" src="../assets/plus.svg" v-on:click="showFormInput = !showFormInput">
         <p class="touch-me">Creer un nouveau dossier !</p>
        <div class="product" v-show="showFormInput" style="display:flex; justify-content:center;margin:auto;padding-bottom:20px;">
             <label><b>Nom de la ressource</b></label>
             <input type="text" id="name" name="name" v-model="newFolder.name">
          <input type="button" value="Ajouter" @click="addFolder()" class="product-add-cart">
         </div>
    </form>

<!--   <video id="background-video" autoplay loop muted>-->

<!--     <source src="@/assets/coding.mp4" type="video/mp4">-->

<!--   </video>-->

  <video src="@/assets/coding.mp4" autoplay="" muted="" loop="" playsinline=""></video>
  <!-- Formulaire d'ajout de ressources -->
   <div>
  <form id="addResourceForm">

    <img alt="Vue logo" src="../assets/plus.svg" v-on:click="showForm = !showForm">
    <p class="touch-me">Ajouter une ressource !</p>
    <div class="product" v-show="showForm">
      <label><b>Nom de la ressource</b></label>
      <input type="text" id="name" name="name" v-model="newResource.name">
      <label><b>Lien</b></label>
      <input type="text" id="url" name="url" v-model="newResource.url">
      <label><b>Souhaitez vous l'épingler sur la page d'accueil ?</b> </label>
      <!-- Probleme au niveau de la checkbox et de l'image... -->
      <div>
        <label><img v-if ="checkbox" src="@/assets/pinned.png" /><img v-if ="!checkbox" src="@/assets/pin.png" /></label>
        <input type="checkbox" class="text check-form-plus" @click="checkbox = !checkbox">
      </div>
      <div>{{folders.name}}</div>
      <label><b>Souhaitez-vous répertorier votre ressource dans un dossier ?</b></label>
      <select name="folder" id="folder" v-model="newResource.folder_id">
        <option value="0">Aucun dossier</option>
        <option :key="folder.id" v-for="folder in folders" :value="folder.id">{{folder.name}}</option>
      </select>
      <input type="button" value="Ajouter" @click="addResource()" class="product-add-cart">
    </div>
  </form>
   </div>
  <!--Traitement des ressources -->
  <MyResource :resources="resources" :folders="folders"></MyResource>
 </div>
</template>

<script>
// @ is an alias to /src
import MyResource from "@/components/MyResource";
export default {
  name: 'HomeView',
  // Components imported have to be here to :)
  components: {MyResource},
  data() {
    return {
      // Form control
      showForm: false,
      showFormInput: false,
      checkbox: false,
      checkbox_folders: false,
      defaultNewResource: {name: "", url: "", folder_id: 0},
      newResource: {name: "", url: "", folder_id: []},
      // Our data
      resources: [
        {
          id: 1,
          name: "Free System Design PDF",
          url: "https://blog.bytebytego.com/p/free-system-design-pdf-158-pages?s=r",
          pinned: true,
          folder_id: 0
        },
        {
          id: 2,
          name: "Modern Python Setup for Everyday Data Development",
          url: "https://python.plainenglish.io/modern-python-setup-for-everyday-data-development-e1522886e654",
          pinned: false,
          folder_id: 1
        },
        {
          id: 3,
          name: "Python is About to Speed Up Even More",
          url: "https://python.plainenglish.io/python-is-about-to-speed-up-even-more-1003ea1240f0?source=rss----78073def27b8---4",
          pinned: false,
          folder_id: 1
        },
        {
          id: 4,
          name: "How to do Asynchronous Programming in JavaScript?",
          url: "https://aniketprakash.hashnode.dev/how-to-do-asynchronous-programming-in-javascript",
          pinned: true,
          folder_id: 2
        },
        {
          id: 5,
          name: "Functions are the heart of JS",
          url: "https://badolla.hashnode.dev/functions-are-the-heart-of-javascript",
          pinned: false,
          folder_id: 2
        },
        {
          id: 6,
          name: "Introducing KanBoard - Your Personal Project Management Tool ✨🚀",
          url: "https://madza.hashnode.dev/introducing-kanboard-your-personal-project-management-tool",
          pinned: false,
          folder_id: 0
        },
        {
          id: 7,
          name: "Ruby en 20 minutos (ES)",
          url: "https://www.ruby-lang.org/es/documentation/quickstart/",
          pinned: true,
          folder_id: 3
        },
        {
          id: 8,
          name: "Getting started with Ruby On Rails",
          url: "https://guides.rubyonrails.org/getting_started.html",
          pinned: false,
          folder_id: 3
        },
        // Ajout ici, nouvelle ressource
      ],
      folders: [
        {
          id: 1,
          name: "Python",
          color: "blue",
          icon: "https://picsum.photos/48"
        },
        {
          id: 2,
          name: "JavaScript",
          color: "yellow",
          icon: "https://picsum.photos/49"
        },
        {
          id: 3,
          name: "Ruby",
          color: "red",
          icon: "https://picsum.photos/50"
        },
        {
          id: 4,
          name: "Others",
          color: "grey",
          icon: "https://picsum.photos/51"
        }
      ],
      defaultNewFolder: {name: "", color: "grey", icon: "https://picsum.photos/52"},
      newFolder: { name: "", color: "grey", icon: "https://picsum.photos/52" }
    }
  },
  created() {
    this.resources = localStorage.getItem('resources') ? JSON.parse(localStorage.getItem('resources')) : this.resources;
    this.folders = localStorage.getItem('folders') ? JSON.parse(localStorage.getItem('folders')) : this.folders;
  },
  mounted() {
    console.log(this.resources)
    console.log(this.folders)
  },
  methods: {
    addPersister: function () {
      window.localStorage.setItem("resources", JSON.stringify(this.resources));
      window.localStorage.setItem("folders", JSON.stringify(this.folders));
    },
    merge: function (...arr) {
      return arr.reduce((acc, val) => {
        return {...acc, ...val};
      }, {});
    },
    addResource: function () {
      this.resources.push(this.merge({id: this.resources.length + 1}, {pinned: this.checkbox}, this.newResource))
      this.newResource = this.defaultNewResource
      this.addPersister()
    },
    addFolder: function () {
      this.folders.push(this.merge({id: this.folders.length + 1}, this.newFolder))
      this.newFolder = this.defaultNewFolder
      this.addPersister()
      console.log(this.folders)
    }
  }
}

</script>

<style scoped>

#background-video {
  height: 100vh;
  width: 100vw;
  object-fit: cover;
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  z-index: -1;
}

h1, h2, #btnVideo{

  color: white;

  font-family: Trebuchet MS;

  font-weight: bold;

  text-align: center;

}

h1 {
  font-size: 6rem;
  margin-top: 30vh;
}

h2 { font-size: 3rem; }

#btnVideo{
  font-size: 1.5rem;
  background: 0;
  border: 0;
  margin-left: 50%;
  transform: translateX(-50%);
}
#addResourceForm{
  display: flex;
  justify-content: end;
  width: 100%;
  flex-direction: column;
  align-items: flex-end;
  /*position:absolute;*/

}
/*@media screen and (min-width:0px){*/
/*  .container{*/
/*    width:fit-content;*/
/*  }*/

/*}*/
#addResourceForm > img{
  /*width: 20%;*/
  width:fit-content;
  justify-content: flex-end;
  display: flex;
  /*margin: auto;*/


}

.product{
  display: flex;
  justify-content: center;
  flex-direction: column;
  max-width: 12%;
}


/*style lettre devbox*/
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@900&display=swap');

body {
  padding: 0;
  margin: 0;
  height: 100vh;
  background: red;
  font-family: 'Poppins', sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
}

ul {
  position: relative;
}

li {
  list-style: none;
}

label {
  position: relative;
}

input[type="checkbox"] {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 80px;
  width: 80px;
  z-index: 100;
}

.letter {
  position: relative;
  height: 80px;
  width: 80px;
  background: #18191f;
  color: #555;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 46px;
  cursor: pointer;
  margin: 0 4px;
  border-radius: 20px;
  box-shadow: -1px -1px 4px rgba(255, 255, 255, 0.05),
  4px 4px 6px rgba(0, 0, 0, 0.2),
  inset -1px -1px 4px rgba(255, 255, 255, 0.05),
  inset 1px 1px 1px rgba(0, 0, 0, 0.1);
}

/* div:before {
  content: "";
  position: absolute;
  top: 2px;
  left: 2px;
  width: 75px;
  height: 38px;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
  background: rgba(255, 255, 255, 0.05);
} */

input[type="checkbox"]:checked ~ div {
  box-shadow: inset 0 0 2px rgba(255, 255, 255, 0.05),
  inset 4px 4px 6px rgba(0, 0, 0, 0.2);
  color: yellow;
  text-shadow: 0 0 15px yellow, 0 0 25px yellow;
  animation: glow 1.5s linear infinite;

}



@keyframes glow {
  0% {
    filter: hue-rotate(0deg);
  }
  100% {
    filter: hue-rotate(360deg);
  }
}


.check-form-plus{
  opacity: 1 !important;
  height: 16px !important;
  width: 14px !important;
}

#app > div > div.hello > form > img{
  background:white;
  border-radius: 1rem;
}

.my-title-main{
  display:flex;
  justify-content: center;
  padding-bottom:20px;
  font-family: 'Poppins', sans-serif;
}
.touch-me{
  color:white
}
#addResourceForm > img{
  background:white;
  border-radius: 20px;
}
#addResourceForm{
  align-items:center;
}
</style>
