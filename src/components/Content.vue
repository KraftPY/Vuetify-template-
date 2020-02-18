<template>
  <v-container class="main_container">
    <v-row justify="center">
      <v-col cols="12" sm="12" md="4" lg="4" class="py-0 pl-0">
        <v-subheader class="subtitle-2 pl-7">Type of paper needed</v-subheader>
        <v-overflow-btn class="primary--text" outlined :items="dropdown_list">
          <label slot="label" class="black--text font-weight-black"
            >Admission Essay / Application</label
          >
          <v-icon slot="append" class="primary--text mt-1"
            >mdi-arrow-down-bold-circle-outline</v-icon
          >
        </v-overflow-btn>
        <v-text-field solo flat outlined readonly>
          <label slot="label" class="black--text font-weight-black mx-4">{{
            `${page + 1} page = ${(page + 1) * 280} words`
          }}</label>
          <v-icon
            slot="append"
            @click="downPage"
            :color="page > 0 ? 'primary' : 'grey lighten-1'"
            >mdi-minus-circle-outline</v-icon
          >
          <v-icon
            @click="upPage"
            slot="append"
            :color="page < maxPages - 1 ? 'primary' : 'grey lighten-1'"
            class="mr-4"
            >mdi-plus-circle-outline</v-icon
          >
        </v-text-field>
      </v-col>
      <v-col cols="12" sm="12" md="6" lg="6" class="ma-0 pa-0">
        <Cards v-if="isCheck" />
        <CustomDate v-if="!isCheck" />
      </v-col>
      <v-col cols="12" sm="12" md="2" lg="2" class="ma-0 py-0">
        <v-subheader class="subtitle-2 pl-7"></v-subheader>
        <div class="d-flex flex-column align-end">
          <p class="text--secondary caption mb-2">Tuesday, Nov 27, 19:16</p>
          <p class="black--text display-1 font-weight-black mb-2">
            {{ `$${price}` }}
          </p>
          <v-btn depressed width="100%" height="60" class="red accent-2"
            >Order now</v-btn
          >
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Cards from "@/components/Cards";
import CustomDate from "@/components/CustomDate";

export default {
  name: "Content",
  components: {
    Cards,
    CustomDate
  },
  props: {
    isCheck: Boolean
  },
  data: () => ({
    price: 61.95,
    page: 0,
    maxPages: 4,
    dropdown_list: [
      "Essay",
      "Term Paper",
      "Dissertation & Thesis",
      "Citation Styles",
      "Essay"
    ]
  }),
  methods: {
    upPage() {
      if (this.page < this.maxPages - 1) {
        this.page++;
      }
    },
    downPage() {
      if (this.page > 0) {
        this.page--;
      }
    }
  }
};
</script>

<style lang="css" scoped>
.main_container {
  display: block;
  width: 100%;
  padding: 0px;
  margin: 0 auto;
  max-width: 1300px;
}
</style>
