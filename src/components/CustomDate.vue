<template>
  <div>
    <v-container class="py-0 ma-0">
      <v-row justify="space-between">
        <!-- Date picker -->

        <v-col cols="12" sm="6" md="6" lg="6" class="ma-0 py-0">
          <v-subheader class="subtitle-2 pl-7">Date</v-subheader>
          <v-menu
            v-model="menu1"
            transition="scale-transition"
            offset-y
            max-width="290px"
            min-width="290px"
          >
            <template v-slot:activator="{ on }">
              <v-text-field readonly v-on="on" outlined>
                <label slot="label" class="black--text font-weight-black pl-4">
                  {{ formatDate }}</label
                >
              </v-text-field>
            </template>
            <v-date-picker v-model="date"></v-date-picker>
          </v-menu>
        </v-col>
        <!-- Date picker -->

        <!-- Time picker -->
        <v-col cols="12" sm="6" md="6" lg="6" class="ma-0 py-0">
          <v-subheader class="subtitle-2 pl-7">Time</v-subheader>
          <v-menu
            ref="menu"
            v-model="menu2"
            :close-on-content-click="false"
            :nudge-right="40"
            transition="scale-transition"
            offset-y
            max-width="290px"
            min-width="290px"
          >
            <template v-slot:activator="{ on }">
              <v-text-field v-model="time" readonly v-on="on" outlined="">
                <label slot="label" class="black--text font-weight-black pl-4">
                  {{ formatTime }}
                </label>
              </v-text-field>
            </template>
            <v-time-picker
              v-if="menu2"
              v-model="time"
              full-width
              @click:minute="$refs.menu.save(time)"
            ></v-time-picker>
          </v-menu>
        </v-col>
        <!-- End Time picker -->

        <v-col cols="12" class="ma-0 py-0">
          <v-text-field solo flat outlined readonly>
            <v-icon
              absolute
              slot="append"
              @click="downHours"
              :color="hours > 1 ? 'primary' : 'grey lighten-1'"
              left
              >mdi-minus-circle-outline</v-icon
            >
            <label slot="label" class="black--text font-weight-black mx-4">
              {{ `${hours} hours to deadline` }}
            </label>
            <v-icon
              @click="upHours"
              slot="append"
              :color="hours < maxHours ? 'primary' : 'grey lighten-1'"
              class="mr-4"
              right
              >mdi-plus-circle-outline</v-icon
            >
          </v-text-field>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "CustomDate",
  data: () => ({
    date: new Date().toISOString().substr(0, 10),
    time: null,
    menu1: false,
    menu2: false,
    hours: 1,
    maxHours: 4
  }),
  computed: {
    formatDate() {
      return this.date
        .split("-")
        .reverse()
        .join("-");
    },
    formatTime() {
      return `${new Date().getHours()}:${new Date().getMinutes()}`;
    }
  },
  methods: {
    upHours() {
      if (this.hours < this.maxHours) {
        this.hours++;
      }
    },
    downHours() {
      if (this.hours > 1) {
        this.hours--;
      }
    }
  }
};
</script>

<style lang="scss" scoped></style>
