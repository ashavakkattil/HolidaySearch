<template>
  <div class="searchBar">
    <v-row>
      <v-col xs="12" sm="6" md="4">
        <v-autocomplete
          outlined
          :loading="loading"
          :append-icon="' '"
          label="Where to ?"
          :items="items"
          cache-items
          :search-input.sync="search"
          v-model="select"
          hide-details
          hide-no-data
        ></v-autocomplete>
      </v-col>
      <v-col xs="12" sm="6" md="4">When</v-col>
      <v-col xs="12" md="4">
        <v-btn color="primary">Search</v-btn>
      </v-col>
    </v-row>
  </div>
</template>
<script>
export default {
  data() {
    return {
      items: [],
      search: null,
      select: null,
      loading: false,
      states: [
        "kerala",
        "Tamil Nadu",
        "Karnataka",
        "Andhra",
        "telangana",
        "Goa"
      ]
    };
  },
  watch: {
    search(val) {
      val && val !== this.select && this.querySelections(val);
    }
  },
  methods: {
    querySelections(v) {
      this.loading = true;

      setTimeout(() => {
        this.items = this.states.filter(e => {
          return (e || "").toLowerCase().indexOf((v || "").toLowerCase()) > -1;
        });
        this.loading = false;
      }, 500);
    }
  }
};
</script>

<style scoped>
.searchBar {
  max-width: 50%;
  margin: auto;
  background-color: #eeeeee;
  border-radius: 4px;
  padding: 5px;
}
</style>