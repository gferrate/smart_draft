<template>
  <div>
    <navbar />
    <b-container class="pb-5">
      <b-card class="text-left shadow-sm">
        <template v-slot:header>Sign contract</template>
        <b-card-text>
          <b-row>
            <b-col>
              <h4>Compensation</h4>
              <b-form-textarea
                id="textarea-auto-height"
                placeholder="Fill"
                v-model="contract.compensation"
                rows="5"
                max-rows="25"
                disabled
              ></b-form-textarea>
              <h4 class="mt-4">Event Logistics</h4>
              <b-form-textarea
                id="textarea-auto-height"
                placeholder="Fill"
                v-model="contract.logistics"
                rows="5"
                max-rows="25"
                disabled
              ></b-form-textarea>
              <h4 class="mt-4">Professional Appearance</h4>
              <b-form-textarea
                id="textarea-auto-height"
                placeholder="Fill"
                v-model="contract.appearance"
                rows="5"
                max-rows="25"
                disabled
              ></b-form-textarea>
              <h4 class="mt-4">Signatures</h4>
              <b-form-group id="input-group-1" label="Client:" label-for="input-1">
                <b-form-input id="input-1" type="text" disabled></b-form-input>
              </b-form-group>
              <b-form-group id="input-group-1" label="Vendor:" label-for="input-1">
                <b-form-input
                  id="input-1"
                  type="text"
                  v-model="signature"
                  :state="signatureState"
                  aria-describedby="input-live-help input-live-feedback"
                ></b-form-input>
              </b-form-group>
            </b-col>
          </b-row>
          <b-row class="text-center border-top pt-3">
            <b-col class="text-center">
              <b-button
                variant="outline-primary"
                class="shadow-sm"
                to="/senior_lawyer_case_files"
              >Back to Case Files</b-button>
              <b-button
                v-b-modal.modal-1
                variant="outline-primary"
                class="shadow-sm ml-2"
              >Download as xlsx</b-button>
              <b-modal id="modal-1" hide-footer>
                <p>Simulation of Word document downloading</p>
              </b-modal>
              <b-button
                class="shadow-sm ml-2"
                to="/finalized_contract_oposing_party"
              >Sign and send to oposing party</b-button>
            </b-col>
          </b-row>
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
  computed: {
    signatureState() {
      return this.signature.length > 0 ? true : false;
    }
  },
  data() {
    return {
      signature: '',
      selected: ["nda"], // Must be an array reference!
      options: [
        { text: "NDA", value: "nda" },
        { text: "Patent", value: "patent" },
        { text: "Other type", value: "other" }
      ],
      contract: {
        compensation:
          "In exchange for the services described above, the Client agrees to provide the Vendor with a total payment sum of $240. A non-refundable fee of 20% of this amount or $23 shall be paid upon the execution of this contract, with the balance due no less than five (5) business days prior to the Event.",
        logistics:
          "The Vendor shall have access to the Event location beginning at 16:00 on 2020-01-02  in order to set up the appropriate stations, goods, or other items necessary in order to complete the services described. \nItems that require physical display space must be no larger than 24m and shall be displayed in a clean and orderly fashion throughout the course of the Event. No goods or services not described above may be sold or distributed during this Event without the Client’s express written consent.\n Following the event, the Vendor will have until 24h to break down all equipment and clear the area of all goods. The Vendor is required to leave the area in a clean and serviceable manner.",
        appearance:
          "The Vendor will display an appearance and manner appropriate with the mood and theme of the Event being held. The vending station will not in any way interfere with the Event on hand, nor will vending staff leave the station unattended. Any special dress or appearance requirements outside of the accepted norm will be discussed in advance between the Client and the Vendor.\nBy signing below, both the Client and the Vendor indicate that they have read, understand, and agree to all terms and conditions outlined in this contract.",
        comments: "We should rethink the compensation fees.",
        comment_response:
          "The proposed compensation fee is adequate for this client.",
        new_comment: "Okey! I'll update the numbers then."
      }
    };
  }
};
</script>

<style>
#contract {
  width: 100%;
}
</style>
