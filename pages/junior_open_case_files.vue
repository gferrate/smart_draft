<template>
  <div>
    <navbar />
    <b-container>
      <div class="d-flex align-items-center justify-content-between mb-5">
        <response-time-chart :data="chart_3_data" :title="chart_3_title" :labels="chart_3_labels" />
        <contract-status-chart
          :data="chart_1_data"
          :title="chart_1_title"
          :labels="chart_1_labels"
        />
        <response-time-chart :data="chart_2_data" :title="chart_2_title" :labels="chart_2_labels" />
      </div>
      <b-modal id="calendar">
        <div class="text-center">
          <p>Select date to be reminded</p>
          <b-calendar locale="en-US"></b-calendar>
        </div>
      </b-modal>
      <div class="d-flex align-items-center justify-content-between mb-2">
        <h2 class="mb-0">Case files</h2>
        <div>
          <!--<b-button size="sm" class="shadow-sm" to="/contract_repository">
            <b-icon-archive class="mr-2" />Contract repository
          </b-button>-->
          <b-button size="sm" class="shadow-sm" to="/new_case_file">
            <b-icon-file-plus class="mr-2" />Create new case file
          </b-button>
        </div>
      </div>
      <div>
        <b-card no-body class="shadow-sm">
          <b-tabs card>
            <b-tab active>
              <template v-slot:title>
                In progress
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
                      <b-button
                        v-b-modal.calendar
                        variant="outline-primary"
                        sixe="xs"
                        pill
                        class="shadow-sm ml-2 mr-2"
                      >
                        <b-icon-calendar class="mr-2" />Reminder
                      </b-button>
                      <b-button
                        size="xs"
                        pill
                        variant="outline-secondary shadow-sm"
                        to="/fill_template"
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
                Waiting to be approved
                <b-badge>{{ length }}</b-badge>
              </template>
              <b-card-text>
                <b-list-group>
                  <b-list-group-item
                    v-for="(case_name, index) in cases"
                    :key="`case-${index}`"
                    class="d-flex align-items-center justify-content-between"
                  >
                    {{case_name}}
                    <div>
                      <b-button
                        v-b-modal.calendar
                        variant="outline-primary"
                        sixe="xs"
                        pill
                        class="shadow-sm ml-2 mr-2"
                      >
                        <b-icon-calendar class="mr-2" />Reminder
                      </b-button>
                      <b-button
                        size="xs"
                        pill
                        variant="outline-secondary shadow-sm"
                        to="send_for_review"
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
                      <b-button
                        size="xs"
                        pill
                        variant="outline-secondary shadow-sm"
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
  data() {
    return {
      chart_1_data: [3, 4, 5],
      chart_1_labels: ["On Progress", "Waiting to be approved", "Finished"],
      chart_1_title: "Case file statuses",
      chart_2_data: [4, 5, 3],
      chart_2_labels: ["Two weeks ago", "Last week", "This week"],
      chart_2_title: "Response times",
      chart_3_data: [3, 3, 4],
      chart_3_labels: ["Two weeks ago", "Last week", "This week"],
      chart_3_title: "Number of revisions per case",
      cal: "",
      in_progress: ["Work contract", "Contract of Service", "Supply"],
      cases: ["Case 1: NDA for Intern", "Case 2: Contract of employment"],
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
.charts {
  height: 280px;
}
</style>
