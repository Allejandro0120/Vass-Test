<template>
  <v-app>
    <v-app-bar
      app
      color="white"
      dark
      height="100vh"
    >
      <div class="d-flex align-center">
        <v-img
          alt="Principal Logo"
          class="shrink mr-1"
          contain
          src="@/assets/sneak_logo.png"
          transition="scale-transition"
          width="40"
        />
        <v-img
          alt="Principal Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="@/assets/sneak_text.png"
          width="150"
        />
      </div>

      <v-spacer></v-spacer>
      <v-row>
        <v-col class="d-flex justify-end">
          <v-btn
            href="#"
            text
            color="rgba(252,117,140)"
          >
            <span class="mr-2">Inicio</span>
          </v-btn>
          <v-btn
            href="#"
            text
            color="rgba(252,117,140)"
          >
            <span class="mr-2">Noticias</span>
          </v-btn>
          <v-btn
            href="#"
            text
            color="rgba(252,117,140)"
          >
            <span class="mr-2">Contacto</span>
          </v-btn>
        </v-col>  
      </v-row>
    </v-app-bar>

    <v-main>
      <Home/>
    </v-main>
  </v-app>
</template>

<script>
import Home from './components/Home';

export default {
  name: 'App',

  components: {
    Home,
  },

  data: () => ({
    //
  }),
};
</script>
