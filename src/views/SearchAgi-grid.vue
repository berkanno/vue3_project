<template>
  <v-card color="black" class="mx-4 my-1">
    <v-container>
      <v-row justify="center">
        <v-col cols="6">
          <v-card color="grey-darken-4" class="pa-5 mt-5">
            <v-text-field
              color="white"
              label="foodSearch"
              placeholder="burgers"
              v-model="foodSearch"
            ></v-text-field>
            <v-row justify="center">
              <v-btn
                @click="findFood()"
                color="cyan-accent-2"
                class="mx-16"
                rounded
                >Search</v-btn
              >
            </v-row>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
    <v-container>
      <v-row justify="center">
        <v-col cols="6">
          <v-card class="px-4 py-1 mt-4 mb-12" color="grey-darken-4" v-show="!göster">
            <ul style="color: aqua" v-for="item in listFoodName" :key="item">
              <li style="text-align: center">{{ item }}</li>
            </ul>
          </v-card>
        </v-col>
      </v-row>
    </v-container>

    <ag-grid-vue
      class="ag-theme-alpine"
      style="
        height: 400px;
        width: 822px;
        margin: auto;
        margin-bottom: 7px;
        padding-right: 3px;
      "
      :columnDefs="columnDefs"
      :rowData="rowData"
      v-show="göster"
    >
    </ag-grid-vue>
  </v-card>
</template>

<script>
import { AgGridVue } from "ag-grid-vue3";

import "ag-grid-community/styles/ag-grid.css";
import "ag-grid-community/styles/ag-theme-alpine.css";

export default {
  name: "App",
  data() {
    return {
      columnDefs: null,
      rowData: null,
      foodSearch: "",
      göster: false,
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
    findFood() {
      this.göster = true;
      this.columnDefs = [
        { field: "name", sortable: true, filter: true },
        { field: "price", sortable: true, filter: true },
        { field: "rate", sortable: true, filter: true },
        { field: "country", sortable: true, filter: true },
      ];
      fetch(
        "https://free-food-menus-api-production.up.railway.app/" +
          this.foodSearch
      )
        .then((result) => result.json())
        .then((rowData) => (this.rowData = rowData));
    },
  },
  components: {
    AgGridVue,
  },
};
</script>

<style scoped></style>
