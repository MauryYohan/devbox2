<template>
  <!-- Formulaire d'ajout de ressources -->
  <form id="addResourceForm">
    <img alt="Vue logo" src="../assets/plus.svg" v-on:click="showForm = !showForm">Touch me !
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
  <!--Traitement des ressources -->
  <MyResource :resources="resources" :folders="folders"></MyResource>
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
      checkbox: false,
      checkbox_folders : false,
      defaultNewResource: {name:"", url:"", folder_id:0},
      newResource: {name:"", url:"", folder_id:[]},
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
      ]
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
    addPersister: function() {
      window.localStorage.setItem("resources", JSON.stringify(this.resources));
      window.localStorage.setItem("folders", JSON.stringify(this.folders));
    },
    merge: function(...arr){
      return arr.reduce((acc, val) => {
        return { ...acc, ...val  };
        }, {});
    },
    addResource: function() {
      this.resources.push(this.merge({id: this.resources.length + 1}, {pinned: this.checkbox}, this.newResource))
      this.newResource = this.defaultNewResource
      this.addPersister()
    }
  }
}
</script>
