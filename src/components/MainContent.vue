<template>
  <v-container fluid>
    <v-layout row wrap align-center>
      <v-flex v-for="article in articles" :key="article.title" xs12 md6>
        <div order-md2>
          <v-card class="ma-3" hover data-aos="zoom-out-down" data-aos-easing="ease">
            <v-responsive>
              <v-img height="350px" v-bind:src="article.urlToImage"></v-img>
              <v-container fill-height fluid>
                <v-layout>
                  <v-flex xs12 align-start d-flex>
                    <span class="headline">{{ article.title }}</span>
                  </v-flex>
                </v-layout>
              </v-container>
            </v-responsive>
            <v-card-text>{{ article.description }}</v-card-text>
            <v-card-actions>
              <v-avatar size="32px">
                <img class="img-circle elevation-7 mb-1" :src="getImgUrl(article.source.id)">
              </v-avatar>
              <v-chip small class="dark--text">{{article.source.name}}</v-chip>
              <v-spacer></v-spacer>
              <!-- <v-chip small color="blue lighten-1" class="dark--text">{{article.author}}</v-chip>
              <v-spacer></v-spacer>-->
              <v-btn
                small
                replace
                color="primary"
                v-bind:href="article.url"
                target="_blank"
              >Read More</v-btn>
            </v-card-actions>
          </v-card>
        </div>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  props: {
    articles: Array
  },

  methods: {
    getImgUrl(pic) {
      return require("../assets/images/" + pic + ".png");
    }
  }
};
</script>