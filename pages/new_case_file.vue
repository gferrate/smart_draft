<template>
  <div>
    <navbar />
    <b-container>
      <b-row class="text-center">
        <b-col>
          <div>
            <b-card class="text-left shadow-sm">
              <template v-slot:header>Template selection</template>
              <b-card-text>
                <b-form-group label="Filters">
                  <b-form-checkbox-group v-model="selected" :options="options" switches stacked></b-form-checkbox-group>
                </b-form-group>
                <b-form-group id="input-group-1" label="Search by keywords:" label-for="input-1">
                  <b-form-input id="input-1" type="text"></b-form-input>
                </b-form-group>
                Results:
                <b-list-group>
                    <b-list-group-item
                      v-for="(case_name, index) in cases"
                      :key="`case-${index}`"
                      class="d-flex align-items-center justify-content-between"
                    >
                      {{case_name}}
                      <b-button size="sm" pill variant="outline-secondary">Select</b-button>
                    </b-list-group-item>
                </b-list-group>
              </b-card-text>
            </b-card>
          </div>
        </b-col>
        <b-col>
          <b-card class="text-left shadow-sm">
            <template v-slot:header>
              <div class="d-flex align-items-center justify-content-between">
                Contract preview
                <b-button size="sm" class="shadow-sm" to="/fill_template">Fill contract</b-button>
              </div>
            </template>
            <b-card-text>
              <img id="contract" src="~/assets/contract.png" alt="Contract" />
            </b-card-text>
          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Navbar from "~/components/Navbar.vue";

export default {
  components: {
    Navbar
  },
  data() {
    return {
      selected_template: null,
      cases: ["Work contract", "Contract of Service", "Supply"],
      selected: ["nda"], // Must be an array reference!
      options: [
        { text: "NDA", value: "nda" },
        { text: "Patent", value: "patent" },
        { text: "Other type", value: "other" }
      ]
    };
  }
};
</script>

<style>
#contract {
  width: 100%;
}
</style>
