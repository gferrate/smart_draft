<template>
  <div>
    <navbar />
    <b-container>
      <div class="d-flex align-items-center justify-content-between mb-2">
        <h2 class="mb-0">Case files</h2>
        <b-button size="sm" class="shadow-sm" href="/new_case_file">
          <b-icon-file-plus class="mr-2" />Create new case file
        </b-button>
      </div>
      <div>
        <b-card no-body class="shadow-sm">
          <b-tabs card>
            <b-tab active>
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
                    <b-button size="xs" pill variant="outline-secondary">Open</b-button>
                  </b-list-group-item>
                </b-list-group>
              </b-card-text>
            </b-tab>
            <b-tab title="Finished">
              <b-card-text>Tab contents 2</b-card-text>
            </b-tab>
          </b-tabs>
        </b-card>
      </div>
    </b-container>
  </div>
</template>

<script>
import Navbar from "~/components/Navbar.vue";
import { BIconFilePlus } from "bootstrap-vue";

export default {
  components: {
    Navbar,
    BIconFilePlus
  },
  data() {
    return {
      cases: ["Case 1", "Case 2"]
    };
  },
  computed: {
    length() {
      return this.cases.length;
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
