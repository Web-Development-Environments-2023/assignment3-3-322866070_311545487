<template>
  <div class="container">
    <b-tabs content-class="mt-3" justified>
      <b-tab v-for="r in this.recipes" :key="r" :title="r.title"><FamilyRecipePreview :recipe="r"/></b-tab>
    </b-tabs>
  </div>
</template>

<script>
import FamilyRecipePreview from "../components/FamilyRecipePreview";
export default {
  name: "FamilyRecipes",
  components: {
    FamilyRecipePreview
  },
  data(){
    return {
            "recipes": []
    }
  },
  mounted() {
    this.recipes.push( {
      picture:"https://i.ibb.co/0t8hBfC/ezion-marak-kneidalahc.jpg",
      name:"Kneidlach Soup",
      time_to_prepare:25,
      title:"Kneidlach Soup",
      vegeterian: false,
      ingridients:[{"index": "1", "original":"2-3 Chicken wings"}, 
                   {"index": "2", "original":"1 Onion"}, 
                   {"index": "3", "original":"1 Carrot"}, 
                   {"index": "4", "original":"1 glass of carbonated water (Soda)"}, 
                   {"index": "5", "original":"1/2 glass of water"}, 
                   {"index": "6", "original":"1/4 glass of vegetable oil"}, 
                   {"index": "7", "original":"3 eggs"}, 
                   {"index": "8", "original":"2 cups of matzah flour"}, 
                   {"index": "9", "original": "chicken broth"}, 
                   {"index": "10", "original":"salt and pepper"}],
      instructions:[{"index": "1", "step":"First we begin with the soup, cut the carrot and onion."},
                    {"index": "2", "step":"Add to a pot filled 2/3 with cold water the onions, carrot, chicken wings, chicken broth, salt and pepper"}, 
                    {"index": "3", "step":"Boil once and then put on low temperature"}, 
                    {"index": "4", "step":"Now we'll make the Kneidlach. In a bowl put the matzah flour, salt, pepper, carbonated water, water, vegetable oil, eggs and mix everything together"},
                    {"index": "5", "step":"Make the Kneidlach balls and put them in the soup. Cook for 5-7 Minutes"}
                    ],  
      number_of_servings: 8,
      glutenFree: false,
      creator: "Grandmother Susana"
    });
    this.recipes.push( {
        picture:"https://i.ibb.co/wBC9ChX/IMG-3818.jpg",
        name:"Chraime",
        time_to_prepare:30,
        title:"Chraime",
        vegeterian: false,
        ingridients:[{"index": "1", "original":"2 heaping tablespoons spicy paprika"}, 
                     {"index": "2", "original":"2 and 1/2 heaping tablespoon paprika"}, 
                     {"index": "3", "original":"1/2 tablespoon salt"}, 
                     {"index": "4", "original":"16 cloves garlic, minced"}, 
                     {"index": "5", "original":"2 and 1/2 glass of water"}, 
                     {"index": "6", "original":"1/2 glass of vegetable oil"}, 
                     {"index": "7", "original":"1 teaspoon cumin"}, 
                     {"index": "8", "original":"1 teaspoon ground caraway"}, 
                     {"index": "9", "original": "juice from 1 lemon"},
                     {"index": "10", "original":"200g tomato paste"}, 
                     {"index": "11", "original":"6 servings of any fish. Flathead grey mullet (Buri) is recommended"}
                     ],
        instructions:[{"index": "1", "step":"In a bowl put the paprika, spicy paprika, salt minced garlic and 1 glass of water. Mix everything together."},
                      {"index": "2", "step":"Add the vegetable oil to a low and wide pot, add the mixed spices and garlic and cook on medium heat for 2-3 minutes. Cover the pot and continue cooking for 3 minutes."}, 
                      {"index": "3", "step":"Add the tomato paste and another glass of water, cook on medium heat for 5-7 minutes"}, 
                      {"index": "4", "step":"Add the cumin, ground caraway, lemon juice, and the rest of the water. Boil once."},
                      {"index": "5", "step":"Put in an orderly manner the fish, cover the whole fish in sauce, cook for 20 minutes on low heat."},
                      {"index": "6", "step":"Serve with bread."}
                      ],  
        number_of_servings: 6,
        glutenFree: true,
        creator: "Grandmother Moly"
      });
      this.recipes.push( {
        picture:"https://i.ibb.co/Bq5rzjb/b77ca3-dd7e3b9c94fe421794ff72917d19db95-mv2.jpg",
        name:"Marduma",
        time_to_prepare:45,
        title:"Marduma",
        vegeterian: true,
        ingridients:[{"index": "1", "original":"10 medium-size tomatoes"}, 
                     {"index": "2", "original":"1 hot green pepper"}, 
                     {"index": "3", "original":"6 cloves garlic"}, 
                     {"index": "4", "original":"1 green pepper"}, 
                     {"index": "5", "original":"1 tablespoon salt"}, 
                     {"index": "6", "original":"1/2 glass of vegetable oil"}
                     ],
        instructions:[{"index": "1", "step":"Add the vegetable oil to a pot, add all the peppers and cook on high heat for 2-3 minutes. Cover the pot and continue cooking for 2 minutes."},
                      {"index": "2", "step":"Add the tomatoes, garlic, salt and cook on high heat for 5 minutes"}, 
                      {"index": "3", "step":"Add 1/3 a glass of water and mix. Boil once."}, 
                      {"index": "4", "step":"Cook for 35 minutes on low heat."}
                      ],  
        number_of_servings: 6,
        glutenFree: true,
        creator: "Grandmother Moly"
      });
  }
};
</script>
<style lang="scss" scoped>
.container {
  max-width: 1300px;
}
.wrapper {
  display: flex;
}
.wrapped {
  width: 50%;
}
.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
}
</style>
