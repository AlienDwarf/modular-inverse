<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <div class="text-center"></div>
      <v-card>
        <v-card-title class="headline">
          Find inverse of an integer x under modulo m
        </v-card-title>
        <v-card-text>
          <v-text-field label="Integer x: " v-model="x" @input="reset" />
          <v-text-field label="Modulo m: " v-model="m" @input="reset" />
          <div class="text-center">
            <div class="text-h6" v-if="result">
              <v-alert type="success">
                {{ result }}
              </v-alert>
            </div>
            <div class="text-h6" v-else-if="error">
              <v-alert type="warning">
                {{ error }}
              </v-alert>
            </div>
          </div>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn color="primary" @click="calculateInverse">
            Find inverse
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import Logo from "~/components/Logo.vue";
import VuetifyLogo from "~/components/VuetifyLogo.vue";

export default {
  components: {
    Logo,
    VuetifyLogo
  },
  data: () => {
    return {
      x: null,
      m: null,
      error: "",
      result: null,
      loading: false
    };
  },
  methods: {
    calculateInverse() {
      this.error = "";
      this.result = null;
      let x = this.x;
      const m = this.m;

      if (x >= m) x = x % m;

      for (let i = 1; i < m; i++) {
        console.log(x + " " + m);
        if ((x * i) % m == 1) {
          this.loading = false;
          return (this.result = i);
        }
      }
      return (this.error = `${this.x} has no multiplicative inverse under modulo ${this.m}`);
    },
    log() {
      console.log(this.$data);
    },
    reset() {
      this.error = "";
      this.result = null;
    }
  }
};
</script>
