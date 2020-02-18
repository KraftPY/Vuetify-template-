<template>
  <v-app class="grey light-4">
    <!-- Header -->

    <v-app-bar app absolute flat height="130px" class="transparent">
      <v-container class="main_container">
        <v-row class="ma-0 pa-0" no-gutters="">
          <v-col cols="12" sm="6" md="6" lg="6" class="ma-0 pa-0">
            <v-toolbar-title>
              <span class="display-3 font-weight-medium ">Calculator</span>
            </v-toolbar-title>
          </v-col>
          <v-spacer></v-spacer>
          <v-col cols="auto">
            <div class="d-flex justify-start mt-6 mr-6">
              <label for="top-switcher" class="font-weight-medium">
                Custom due date
              </label>
              <v-switch
                v-model="isCheck"
                id="top-switcher"
                right
                class=" ml-2"
              ></v-switch>
            </div>
          </v-col>
        </v-row>
      </v-container>
      <template v-slot:extension>
        <v-tabs show-arrows centered background-color="grey lighten-4">
          <v-tab class="black--text" v-for="(item, i) in menuItems" :key="i">
            {{ item }}
          </v-tab>
        </v-tabs>
      </template>
    </v-app-bar>
    <!-- End Header -->
    <v-content>
      <Content v-bind:isCheck="isCheck" />
    </v-content>
  </v-app>
</template>

<script>
import Content from "./components/Content";

export default {
  name: "App",

  components: {
    Content
  },
  data: () => ({
    menuItems: [
      "High School",
      "College / University - Freshman",
      "College / University - Sophomore",
      "College / University - Junior",
      "College / University - Senior"
    ],
    isCheck: false
  })
};
</script>

<style scoped>
.main_container {
  display: block;
  width: 100%;
  padding: 0px;
  margin: 0 auto;
  max-width: 1300px;
}
</style>
