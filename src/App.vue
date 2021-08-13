<template>
  <v-app id="inspire">
    <v-navigation-drawer 
		v-model="drawer"
		app
	>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            Vue Daily Task
          </v-list-item-title>
          <v-list-item-subtitle>
            Best Todo Ever !
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
		  :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <!-- <v-app-bar app>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>Application</v-toolbar-title>
    </v-app-bar> -->

	<v-app-bar
      app
      color="#e62a00"
      dark
      shrink-on-scroll
      src="https://cdn.pixabay.com/photo/2016/09/01/19/53/pocket-watch-1637396__340.jpg"
	  prominent
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>

      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-app-bar-title>Vue & Vuetify Daily Task</v-app-bar-title>

      <v-spacer></v-spacer>

    </v-app-bar>
	
    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    data: () => ({ 
		items: [
          { title: 'Todo', icon: 'mdi-format-list-checks', to:'/' },
          { title: 'About', icon: 'mdi-help-box', to:'/about' },
        ],
		drawer: null 
	}),
  }
</script>