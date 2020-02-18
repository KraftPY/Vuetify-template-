<template>
  <div>
    <v-subheader class="subtitle-2 pl-7"></v-subheader>
    <v-item-group>
      <v-container class="py-0">
        <v-row justify="space-between" class="flex-nowrap">
          <v-col v-for="(card, i) in cards" :key="i" class="py-0 ma-0">
            <v-item v-slot:default="{ active, toggle }">
              <v-card
                :color="active ? 'blue darken-1' : ''"
                :dark="active ? true : false"
                outlined
                @click="toggle"
                height="143"
                class="d-flex flex-column justify-center align-center"
              >
                <p class="caption ma-0">{{ card.date }}</p>
                <p class="subtitle-1 font-weight-black ma-0">
                  {{ card.hours }}
                </p>
                <p class="subtitle-1 font-weight-black ma-0">
                  {{ `$${card.price}` }}
                </p>
                <p class="caption ma-0">{{ card.page }}</p>
              </v-card>
            </v-item>
          </v-col>
        </v-row>
      </v-container>
    </v-item-group>
  </div>
</template>

<script>
export default {
  name: "Cards",

  data: () => ({
    cards: [
      { date: "27 nov", hours: "12 hours", price: "35.76", page: "Page" },
      { date: "27 nov", hours: "10 hours", price: "38.76", page: "Page" },
      { date: "27 nov", hours: "3 hours", price: "61.95", page: "Page" },
      { date: "27 nov", hours: "6 hours", price: "51.95", page: "Page" },
      { date: "27 nov", hours: "8 hours", price: "40.34", page: "Page" }
    ]
  })
};
</script>

<style scoped></style>
