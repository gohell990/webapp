<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <v-avatar
        color="#FECC00"
        size="56"
        
      >
        XMIY
      </v-avatar>
    </v-app-bar>
    <v-main>
      <v-breadcrumbs
        divider="/"
        link
      >
        <v-breadcrumbs-item to="/">Home</v-breadcrumbs-item>
        <v-breadcrumbs-item v-for="link in links" :key="link.path" :to="link.path" link>H{{link.path}}</v-breadcrumbs-item>
      
      </v-breadcrumbs>
      
    
      <router-view></router-view>
    </v-main>

    
    <v-bottom-navigation
      
      color="primary"
    >
      
      
      <v-btn icon to="/about">
        <span>Recents</span>
        <v-icon>mdi-history</v-icon>
      </v-btn>
      <v-btn icon to="/">
        <span>Favourites</span>
        <v-icon>mdi-heart</v-icon>
      </v-btn>
      <v-btn icon to="/home">
        <span>Nearby</span>
        <v-icon>mdi-map-marker</v-icon>
      </v-btn>
      <v-btn icon to="/home">
        <span>Account</span>
        <v-icon>mdi-account</v-icon>
      </v-btn>
     
    </v-bottom-navigation>

    
  </v-app>
</template>

<script>
  export default{
    data (){
      return {
        navigations: [
          { title:"Recents", icon:"mdi-history", to:'/about'},
          { title:"Favourites", icon:"mdi-heart", to:'/'},
          { title:"Nearby", icon:"mdi-map-marker", to:"/about"}
        ],
        links: [],

      }

    },
    methods:{
      getRoute(){
        this.links = this.$route.matched;
        console.log(this.$route)
      }
    },
    created(){
      this.getRoute();
    }
  }

</script>