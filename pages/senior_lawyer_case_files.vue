<template>
  <div>
    <navbar />
    <b-container class="pb-5">
      <div class="d-flex align-items-center justify-content-between mb-5">
        <response-time-chart :data="chart_3_data" :title="chart_3_title" :labels="chart_3_labels" />
        <contract-status-chart
          :data="chart_1_data"
          :title="chart_1_title"
          :labels="chart_1_labels"
        />
        <response-time-chart :data="chart_2_data" :title="chart_2_title" :labels="chart_2_labels" />
      </div>
      <div class="d-flex align-items-center justify-content-between mb-2">
        <h2 class="mb-0">Case files</h2>
        <div>
          <b-button size="sm" class="shadow-sm" variant="primary" to="/contract_repository">
            <b-icon-archive class="mr-2" />Contract repository
          </b-button>
          <b-button size="sm" class="shadow-sm" to="/new_case_file_senior">
            <b-icon-file-plus class="mr-2" />Create new case file
          </b-button>
        </div>
      </div>
      <div>
        <b-modal id="calendar">
          <div class="text-center">
            <p>Select date to be reminded</p>
            <b-calendar locale="en-US"></b-calendar>
          </div>
        </b-modal>
        <b-card no-body class="shadow-sm">
          <b-tabs card>
            <b-tab active>
              <template v-slot:title>
                To review
                <b-badge>{{ in_progress_length }}</b-badge>
              </template>
              <b-card-text>
                <b-list-group>
                  <b-list-group-item
                    v-for="(case_name, index) in in_progress"
                    :key="`case-${index}`"
                    class="d-flex align-items-center justify-content-between"
                  >
                    {{case_name}}
                    <div>
                      <div class="d-inline">
                        <label for="rating-inline">Priority:</label>
                        <b-form-rating size="sm" id="rating-inline" stars="3" inline value="2"></b-form-rating>
                      </div>
                      <b-button
                        v-b-modal.calendar
                        variant="outline-primary"
                        size="sm"
                        pill
                        class="shadow-sm ml-2 mr-2"
                      >
                        <b-icon-calendar class="mr-2" />Reminder
                      </b-button>
                      <b-button
                        size="sm"
                        pill
                        variant="outline-secondary shadow-sm"
                        to="fill_template_senior"
                      >
                        <b-icon-box-arrow-in-up-right class="mr-2" />Open
                      </b-button>
                    </div>
                  </b-list-group-item>
                </b-list-group>
              </b-card-text>
            </b-tab>
            <b-tab>
              <template v-slot:title>
                Waiting oposing party to sign
                <b-badge>{{ in_progress_length }}</b-badge>
              </template>
              <b-card-text>
                <b-list-group>
                  <b-list-group-item
                    v-for="(case_name, index) in oposing_party"
                    :key="`case-${index}`"
                    class="d-flex align-items-center justify-content-between"
                  >
                    {{case_name}}
                    <div>
                      <div class="d-inline">
                        <label for="rating-inline">Priority:</label>
                        <b-form-rating size="sm" id="rating-inline" stars="3" inline value="2"></b-form-rating>
                      </div>
                      <b-button
                        v-b-modal.calendar
                        variant="outline-primary"
                        size="sm"
                        pill
                        class="shadow-sm ml-2 mr-2"
                      >
                        <b-icon-calendar class="mr-2" />Reminder
                      </b-button>
                      <b-button
                        size="sm"
                        pill
                        variant="outline-secondary shadow-sm"
                        to="finalized_contract_oposing_party"
                      >
                        <b-icon-box-arrow-in-up-right class="mr-2" />Open
                      </b-button>
                    </div>
                  </b-list-group-item>
                </b-list-group>
              </b-card-text>
            </b-tab>
            <b-tab>
              <template v-slot:title>
                Finished
                <b-badge>{{ finished_length }}</b-badge>
              </template>
              <b-card-text>
                <b-list-group>
                  <b-list-group-item
                    v-for="(case_name, index) in finished_cases"
                    :key="`case-${index}`"
                    class="d-flex align-items-center justify-content-between"
                  >
                    {{case_name}}
                    <div>
                      <div class="d-inline mr-2">
                        <label for="rating-inline">Priority:</label>
                        <b-form-rating size="sm" id="rating-inline" stars="3" inline value="2"></b-form-rating>
                      </div>
                      <b-button
                        size="sm"
                        pill
                        variant="outline-secondary"
                        to="/finalized_contract_signed"
                      >
                        <b-icon-box-arrow-in-up-right class="mr-2" />Open
                      </b-button>
                    </div>
                  </b-list-group-item>
                </b-list-group>
              </b-card-text>
            </b-tab>
          </b-tabs>
        </b-card>
      </div>
      <div>
        <h2 class="mt-4 mb-2">Upcoming reminders</h2>
        <!--<b-card class="shadow-sm text-center"> </b-card>-->
        <b-calendar :date-info-fn="dateClass" locale="en"></b-calendar>
      </div>
    </b-container>
  </div>
</template>

<script>
import Navbar from "~/components/Navbar.vue";
import {
  BIconFilePlus,
  BIconArchive,
  BIconCalendar,
  BIconBoxArrowInUpRight
} from "bootstrap-vue";
import PieChart from "~/components/PieChart";
import ContractStatusChart from "~/components/charts/ContractStatusChart";
import ResponseTimeChart from "~/components/charts/ResponseTimeChart";

export default {
  components: {
    Navbar,
    BIconFilePlus,
    BIconArchive,
    BIconCalendar,
    BIconBoxArrowInUpRight,
    ContractStatusChart,
    ResponseTimeChart,
    PieChart
  },
  methods: {
    dateClass(ymd, date) {
      const day = date.getDate();
      return day == 10 || day == 20 || day == 15 || day == 1
        ? "table-info"
        : "";
    }
  },
  data() {
    return {
      chart_1_data: [3, 3, 4],
      chart_1_labels: ["NDA", "Contract of service", "Contract of work"],
      chart_1_title: "Number of clients",
      chart_2_data: [4, 5, 3],
      chart_2_labels: ["Two weeks ago", "Last week", "This week"],
      chart_2_title: "Completed cases",
      chart_3_data: [3, 3, 4],
      chart_3_labels: ["Two weeks ago", "Last week", "This week"],
      chart_3_title: "Client retention",
      in_progress: ["Work contract", "Contract of Service", "Supply"],
      cases: ["Case 1: NDA for Intern", "Case 2: Contract of employment"],
      oposing_party: [
        "Case 1: NDA for Intern",
        "Case 2: Contract of employment"
      ],
      finished_cases: ["Case 1", "Case 2", "Case 3", "Case 4"]
    };
  },
  computed: {
    length() {
      return this.cases.length;
    },
    finished_length() {
      return this.finished_cases.length;
    },
    in_progress_length() {
      return this.in_progress.length;
    }
  }
};
</script>

<style>
/*.style {
    background-color: #cbcbcc;
    padding-bottom: 10vw;
    height: 80vh;
}
.angle-bottom-left {
    -webkit-clip-path: polygon(0 0,100% 0vw,100% 100%,0 calc(100% - 15vw));
    clip-path: polygon(0 0,100% 0,100% 100%,0 calc(100% - 15vw));
    padding-bottom: 12vh;
}
.angled {
    overflow-x: auto;
    overflow-y: hidden;
    width: 100%;
    left: 0;
    position: relative;
    max-width: 100vw;
    padding-bottom: 3.5rem;
    padding-top: 3rem;
}*/
</style>
