<template lang="html">

  <blog-post
    v-bind:title="post.title + ' par ' + post.author.name"
  ></blog-post>

  <div class="wrapper">
    <div class="profile">
      <div class="profile_img_info">
        <div class="img">
            <img src="user_pic.jpg" alt="profile_pic">
        </div>
        <div class="info">
          <p class="name"> Lucie Dubois </p>
          <p class="place"><span><i class=""></span> Paris </p>
        </div>
      </div>
      <div class="profile_skills">
        <div class="skills">
          <p> Projet </p>
          <ul>
            <li><span class="icon">
              <i class="">
            </span>
                <span class="title"> Chaque seconde, 253 kilos de plastique sont déversés dans les océans. Pour lutter contre la pollution plastique des océans, un autre mastodonte marin suscite lui aussi l'espoir.  </span>
            </li>
            <li><span class="icon"></span>
                <span class="title"> Pour laver les océans, le Manta, un voilier de 70 mètres de long, doit permettre de collecter, trier et compacter en mer une grande quantité de macro-déchets plastiques flottant à la surface des océans.  </span>
            </li>
            <li><span class="icon"></span>
                <span class="title"> Cliquez ici, pour plus de détails </span>
            </li>
          </ul>
        </div>
        <div class="tags_wrap">
          <span class="tag"> écolo </span>
          <span class="tag"> océans </span>
          <span class="tag"> manta </span>
          <span class="tag"> voilier </span>
        </div>
      </div>
    </div>
    <div class="profile_counts">
      <div class="profile_counts_wrap">
        <div class="item">
              <div class="icon">
                <i class="fas fa-thumbs-up" aria-hidden="true">
              </div>
              <div class="title">  2920 views </div>
        </div>
      </div>
      <div class="profile_counts_wrap">
        <div class="item">
              <div class="icon"><i class="fas fa-thumbs-up" aria-hidden="true"></div>
              <div class="title"> 320 likes </div>
        </div>
      </div>
      <div class="profile_counts_wrap">
        <div class="item">
              <div class="icon">
                <i class="fas fa-thumbs-up" aria-hidden="true"></i>
              </div>
              <div class="title"> 117 comments </div>

        </div>
      </div>
    </div>
  </div>

  <div class="video-projet">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/yXEMJSL5rKs" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  </div>


</template>

<script>
export default {
  name: wrapper,
  name: blog-post,
  name: video-projet,

  data(){
    return{
    //on met la data dans une boite vide = restaurants
    projetID: ,
     projet: null,
     nom: "utopia",
     type: "ecolo, social, éducatif",
     investisseurs: false,
     entrepreneurs: false,
     success: false,
     successDelete: false,
     successModify: false,
  }
},

postProjet() {
  const axios = require('axios');
  axios.post(`http://localhost:3000/projet/`, {
      nom: this.nom,
      type: this.type,
  })
  .then(() => {
    this.nom = "";
    this.type = "";
    this.success = true;
  })
  .catch((err) => {
    console.log(err);
  })
},

methods:{
  // on a rajouter async et await pour eviter then et catch
//  async getRestaurants(){

    getProjets(){
    // on définit axios
    const axios = require('axios');
    //on met l'adresse de notre API qu'on veut récupérer format json
    //axios.get('https://restop-toulouse.herokuapp.com/restos')


    //on change d'api pour la suite de l'exo
   axios.get('http://localhost:3000/projets/')
   //on ordonne les données en les mettant dans une petite boite data qui va etre rempli de notre get
   // sachant que le nom du tableau de l'adresse s'appelle data c'est pour ca qu'on a mis data a la fin de response
   .then(response => (this.projets = response.data))




}

</script>

<style lang="css" scoped>
</style>
