<template>
  <span
    :to="{ name: 'recipe', params: { recipeId: recipe.id } }"
    class="recipe-preview"
  >

    <b-card v-if="this.image_load"  >
      <b-card-header align="center"><h5>{{ this.recipe.title }} </h5></b-card-header>
      <br>
      <router-link :to="{ name: 'recipe', params: { recipeId: recipe.id } }">
        <b-card-img 
          :src="this.recipe.image"
          alt="Card image"
          left
          fluid="fluid"
          tag="article"
          style="max-width: 20rem; overflow: auto; display: inline-block;" 
          class="mb-3"
          align="left"
          
        /> 
      </router-link>
      <b-card-text>
        <b-row align="center" style="padding-left: 10px; ">
          <b-col>
            <small>Ready In {{ this.recipe.readyInMinutes }} Minutes </small>
          </b-col>
          <b-col>
            <small>{{ this.recipe.servings }} Servings</small>
          </b-col>
        </b-row>  
        <b-row align="center" style="padding-left: 10px; ">
          <b-col>
            <small>Gluten Free</small>
          </b-col>
          <b-col>
            <small v-if="this.recipe.vegan">Vegan</small>
            <small v-else>Vegetarian</small>
          </b-col>
        </b-row>
        <b-row align="center" style="padding-left: 10px;" >
          <b-col>
            <small v-if="this.recipe.glutenFree"> &#10004; </small>
            <small v-else> &#10008; </small>
          </b-col>
          <b-col >
            <small v-if="this.recipe.vegan"> &#10004; </small>
            <small v-else-if="this.recipe.vegetarian"> &#10004; </small>
            <small v-else> &#10008; </small>
          </b-col>
        </b-row>
        <b-row align="center" style="padding-left: 10px;">
            <b-col><small>Watched</small></b-col>
            <b-col><small>Favorite</small></b-col>
          </b-row>
          <b-row align="center" style="padding-left: 10px;">
            <b-col>
              <small v-if="!$root.store.username"> &#10008; </small>
              <!-- <small v-else-if="wasWatched"> &#10004; </small> -->
              <small v-else> &#10008; </small>
            </b-col>
            <b-col>
              <small v-if="!$root.store.username"> &#10008; </small>
              <!-- <small v-else-if="isFavorite"> &#10004; </small> -->
              <small v-else> &#10008; </small>
            </b-col>
          </b-row>
      </b-card-text>
     
      <div align="center">
        <b-button variant="primary" :to="{ name: 'recipe', params: { recipeId: recipe.id } }" >See Recipe</b-button>
      </div>
      <br>
      
      <b-card-footer class="mb-3" style="margin-top: 6rem">{{ this.recipe.aggregateLikes }} Likes</b-card-footer>
    </b-card>
  </span>
</template>

<script>
export default {
  mounted() {
    this.axios.get(this.recipe.image).then((i) => {
      this.image_load = true;
    });
  },
  data() {
    return {
      image_load: false
    };
  },
  props: {
    recipe: {
      type: Object,
      required: true
    },
    id: {
      type: Number,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    readyInMinutes: {
      type: Number,
      required: true
    },
    image: {
      type: String,
      required: true
    },
    aggregateLikes: {
      type: Number,
      required: false,
      default() {
        return undefined;
      }
    }
  }
};
</script>

<style scoped>
.recipe-preview {
  display: inline-block;
  width: 90%;
  height: 100%;
  position: relative;
  margin: 10px 10px;
}
.recipe-preview > .recipe-body {
  width: 100%;
  height: 200px;
  position: relative;
}
.recipe-preview .recipe-body .recipe-image {
  margin-left: auto;
  margin-right: auto;
  margin-top: auto;
  margin-bottom: auto;
  display: block;
  width: 98%;
  height: auto;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  background-size: cover;
}
.recipe-preview .recipe-footer {
  width: 100%;
  height: 50%;
  overflow: hidden;
}
.recipe-preview .recipe-footer .recipe-title {
  padding: 10px 10px;
  width: 100%;
  font-size: 12pt;
  text-align: left;
  white-space: nowrap;
  overflow: hidden;
  -o-text-overflow: ellipsis;
  text-overflow: ellipsis;
}
.recipe-preview .recipe-footer ul.recipe-overview {
  padding: 5px 10px;
  width: 100%;
  display: -webkit-box;
  display: -moz-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  -o-box-flex: 1;
  box-flex: 1;
  -webkit-flex: 1 auto;
  -ms-flex: 1 auto;
  flex: 1 auto;
  table-layout: fixed;
  margin-bottom: 0px;
}
.recipe-preview .recipe-footer ul.recipe-overview li {
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  -o-box-flex: 1;
  -ms-box-flex: 1;
  box-flex: 1;
  -webkit-flex-grow: 1;
  flex-grow: 1;
  width: 90px;
  display: table-cell;
  text-align: center;
}
</style>
