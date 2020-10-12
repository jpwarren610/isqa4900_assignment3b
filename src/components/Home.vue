<template>
  <v-main>
    <v-container fluid>
      <v-row>
        <v-col align="center" justify="center" cols="12">
          <blockquote>
            Welcome {{validUserName}}!
            <footer>
              <small>
                <em>“If it’s a good movie, the sound could go off and the audience would still have a pretty clear idea of what was going on.” - Alfred Hitchcock</em>
              </small>
            </footer>
          </blockquote>
        </v-col>
      </v-row>
    </v-container>
    <v-container fluid>
      <v-row
        align="center"
        justify="center"
      >
        <v-col 
          cols="12"
            sm="10"
            md="8"
        >
          <v-card class="elevation-2">
            <v-container
              fluid
              grid-list-md
            >
              <v-row>
                <v-col>
                  <v-card>
                    <v-img
                      :src="require('@/assets/images/customer.jpg')" height="200px">
                    </v-img>
                    <v-card-actions>
                      <v-btn class="white--text" flat color="red darken-4" @click="viewMovies">View Movies</v-btn>
                    </v-card-actions>
                  </v-card>
                </v-col>
                <v-col>
                  <v-card>
                  </v-card>
                </v-col>
                <v-col>
                  <v-card>
                  </v-card> 
                </v-col>
              </v-row>
            </v-container>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>
<script>
  import router from '../router';
  export default {
    name: 'Home',
    data: () => ({
      validUserName: "Guest"
    }),
    mounted() {
      this.getUser();
    },
    methods: {
      viewMovies() {
        router.push('/movie-list');
      },
      getUser() {
        if (localStorage.getItem("isAuthenticates")
          && JSON.parse(localStorage.getItem("isAuthenticates")) === true) {
          this.validUserName = JSON.parse(localStorage.getItem("log_user"));
        }
      }
    }
  }
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
