<template>
  <div>
    <v-card
      class="mx-4 mt-1"
      color="grey-darken-4"
      max-width="1220"
      max-height="588"
    >
      <v-img src="@/images/about images/spaghetti.png" max-width="100%">
        <div>
          <div style="margin-left: 10px; padding: 30px">
            <v-card class="ml-5" max-width="250" color="grey-darken-4">
              <div
                style="margin-top: 20px; margin-left: 20px; margin-right: 20px"
              >
                <v-text-field
                  label="Food Name:"
                  placeholder="burgers"
                  type="text"
                  v-model="foodName"
                ></v-text-field>
              </div>
              <div style="margin-left: 20px; margin-bottom: 20px">
                <v-btn
                  @click="getFood()"
                  rounded
                  class="mx-16"
                  color="cyan-accent-2"
                  >Search</v-btn
                >
              </div>
            </v-card>
          </div>
          <div
            style="margin-left: 840px; text-align: center; letter-spacing: 2px"
          >
            <v-card max-width="200" class="px-4 py-1" color="grey-darken-4">
              <ul style="color: aqua" v-for="item in listFoodName" :key="item">
                <li>{{ item }}</li>
              </ul>
            </v-card>
          </div>
        </div>
      </v-img>
    </v-card>
  </div>
  <v-card color="grey-darken-4" class="mx-4 my-1">
    <v-container max-width="600" v-show="show">
      <v-row>
        <v-col v-for="item in foodData" :key="item">
          <v-card class="d-inline-flex">
            <v-card color="grey-darken-4">
              <v-card max-width="300">
                <v-img :src="item.img" max-width="300" cover></v-img>
              </v-card>
              <v-card color="grey-darken-4" max-width="380">
                <v-card-title>
                  <h5 style="display: inline-flex; color: darkturquoise">
                    Name :
                  </h5>
                  {{ item.name }}
                </v-card-title>
                <v-card-title>
                  <h5 style="display: inline-flex; color: darkturquoise">
                    Price :
                  </h5>
                  {{ item.price }}
                </v-card-title>
                <v-card-title>
                  <h5 style="display: inline-flex; color: darkturquoise">
                    Country :
                  </h5>
                  {{ item.country }}
                </v-card-title>
                <v-card-title>
                  <h5 style="display: inline-flex; color: darkturquoise">
                    Rate :
                  </h5>
                  {{ item.rate }}
                </v-card-title>
              </v-card>
            </v-card>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      axiosFood: "",
      foodName: "",
      foodData: [],
      show: "false",
      listFoodName: [
        "bbqs",
        "breads",
        "burgers",
        "chocolates",
        "desserts",
        "drinks",
        "fried-chicken",
        "ice-cream",
        "karides",
        "pizzas",
        "porks",
        "sandwiches",
        "sausages",
        "steaks",
      ],
    };
  },
  methods: {
    showFood() {
      show = true;
    },
    getFood() {
      this.axiosFood =
        "https://free-food-menus-api-production.up.railway.app/" +
        this.foodName;
      axios
        .get(this.axiosFood)
        .then((response) => {
          this.foodData = response.data;
          console.log(this.foodData);
          this.showFood();
        })
        .catch((e) => {
          console.log(e, "hata");
        });
    },
  },
};
</script>

<style></style>
