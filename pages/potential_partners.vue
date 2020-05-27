<template>
  <div>
    <navbar url="/junior_open_case_files" />
    <b-container class="pb-5">
      <b-card class="text-left shadow-sm">
        <template v-slot:header>Potential partners</template>
        <b-card-text>
          <b-card-group deck>
            <div
              :key="index"
              v-for="(partner, index) in partners"
              class="d-inline"
              style="width: 20rem"
            >
              <b-card
                :title="partner.title"
                :img-src="partner.link"
                img-top
                style="max-width: 16rem;"
                class="mb-2 p-3"
              >
                <b-card-text>{{partner.text}}</b-card-text>
              </b-card>
            </div>
          </b-card-group>
        </b-card-text>
      </b-card>
      <b-button
        variant="outline-primary"
        to="/senior_lawyer_case_files"
        class="mt-2"
      >Go back to case files</b-button>
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
      partners: [
        {
          title: "VWO",
          link: "https://static.wingify.com/gcp/images/vwo-logo-color.svg",
          text: "Market-leading A/B testing & conversion optimization platform"
        },
        {
          title: "iDGARD",
          link:
            "data:image/png;base64,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",
          text: "German cloud for secure data exchange & virtual data rooms"
        },
        {
          title: "DocuSign",
          link:
            "https://www.docusign.com/sites/default/files/docusign_logo_black_text_on_white_0.png",
          text:
            "Get the security, mobility, reliability, and ease of use you need to digitally transform your business."
        },
        {
          title: "WebMerge",
          link:
            "https://cdn-main.123contactform.com/wp-content/uploads/2014/06/wm_logo.png",
          text: "Documents's document generation software"
        },
        {
          title: "eBrevia",
          link:
            "https://static1.squarespace.com/static/57251c843c44d8676af995ce/t/572cf432b6aa60ffc680fc36/1462563900795/eBrevia_Icon.png?format=1500w",
          text:
            "Contract analysis, due diligence, LIBOR remediation and lease extraction with unprecedented speed and accuracy."
        },
        {
          title: "Crazyegg",
          link:
            "data:image/png;base64,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",
          text:
            "AB & server side testing, heatmap, session recording, survey & push notification. "
        },
        {
          title: "MouseFlow",
          link:
            "https://en.ryte.com/magazine/wp-content/uploads/2016/08/MF_Logo_Large1.png",
          text:
            "Mouseflow tracks clicks, mouse movement, scrolls, forms, and more."
        },
        {
          title: "SpotDraft",
          link: "https://miro.medium.com/max/3150/0*iFQ_r_cEYwI_0y5q.jpg",
          text: "Artificial Intelligence for your legal paperwork"
        }
      ]
    };
  }
};
</script>

<style>
</style>
