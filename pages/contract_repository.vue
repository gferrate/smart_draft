<template>
  <div>
    <navbar />
    <b-container class="pb-5">
      <b-card class="text-left shadow-sm">
        <template v-slot:header>Contract repository: Historical cases</template>
        <b-card-text>
          <div>
            <b-table striped hover :items="items" :fields="fields">
              <template v-slot:cell(link)="data">
                <b-button
                  pill
                  variant="outline-primary"
                  class="shadow-sm"
                  size="sm"
                  to="/finalized_contract_signed_repository"
                >Details</b-button>
              </template>
            </b-table>
          </div>
        </b-card-text>
      </b-card>
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
      fields: ["contract_name", "lawyer_in_charge", "oposing_party", "completion_date", "link"],
      items: [
        {
          contract_name: "LECARE acquisition",
          lawyer_in_charge: "Lucas Reader",
          completion_date: "2019-03-08",
          link: "",
          oposing_party: "LECARE"
        },
        {
          contract_name: "Contract of Service",
          lawyer_in_charge: "Ramone Frederick",
          completion_date: "2019-12-03",
          link: "",
          oposing_party: "Eicon Technologies"
        },
        {
          contract_name: "Youtube salaries contract",
          lawyer_in_charge: "Elle Randolph",
          completion_date: "2019-12-28",
          link: "",
          oposing_party: "Youtube"
        },
        {
          contract_name: "Work contract",
          lawyer_in_charge: "Lucas Reader",
          completion_date: "2020-01-08",
          link: "",
          oposing_party: "Eiko Infotech"
        },
        {
          contract_name: "NDA Intern",
          lawyer_in_charge: "Elle Randolph",
          completion_date: "2020-01-08",
          link: "",
          oposing_party: "Smart draft"
        },
        {
          contract_name: "New employee contract",
          lawyer_in_charge: "Elle Randolph",
          completion_date: "2020-01-08",
          link: "",
          oposing_party: "Smart draft"
        },
        {
          contract_name: "LECARE acquisition",
          lawyer_in_charge: "Lucas Reader",
          completion_date: "2020-03-08",
          link: "",
          oposing_party: "LECARE"
        }
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
