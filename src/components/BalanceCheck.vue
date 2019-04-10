<template>
  <v-container id="input-usage" grid-list-xl fluid>
    <div v-if="!balance" class="input">
      <h3>Input the IOTA address and IOTA Pay checks the balance</h3>

      <v-form ref="form" v-model="valid" lazy-validation>
        <v-text-field v-model="address" :rules="addressRules" label="IOTA Address" required></v-text-field>

        <v-btn :disabled="!valid" :loading="loading" color="success" @click="validate">Check Balance</v-btn>
      </v-form>
    </div>
    <div v-if="balance" class="result">
      <h2>{{balance}} IOTA</h2>
      <a :href="'https://thetangle.org/address/' + address" target="_blank">Check on TheTangle.org</a>
    </div>
  </v-container>
</template>

<script>
import IOTAPAY from "iotapay";

const iotapay = new IOTAPAY({
  host: "https://nutzdoch.einfachiota.de"
});

export default {
  name: "BalanceCheck",
  data: () => ({
    loading: false,
    valid: false,
    balance: null,
    address: null,
    addressRules: [
      v => !!v || "Address is required",
      v => (v && v.length > 81) || "Address must be more than 81 characters"
    ]
  }),

  methods: {
    validate() {
      if (this.$refs.form.validate()) {
        this.loading = true;
        let self = this;
        iotapay.getBalance([this.address], function(err, balance) {
          if (err) {
            console.log("error:", err);
          }
          console.log("balance:", balance);
          self.balance = balance;
          self.loading = false;
        });
      }
    }
  }
};
</script>
