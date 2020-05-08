<template>
  <div>
    <navbar />
    <b-container class="pb-5">
      <b-card class="text-left shadow-sm">
        <template v-slot:header>Contract repository</template>
        <b-card-text>
          <b-row>
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
  data() {
    return {
      selected: ["nda"], // Must be an array reference!
      options: [
        { text: "NDA", value: "nda" },
        { text: "Patent", value: "patent" },
        { text: "Other type", value: "other" }
      ],
      contract: {
        compensation:
          "In exchange for the services described above, the Client agrees to provide the Vendor with a total payment sum of $[______________]. A non-refundable fee of 20% of this amount or $[______________] shall be paid upon the execution of this contract, with the balance due no less than five (5) business days prior to the Event.",
        logistics:
          "The Vendor shall have access to the Event location beginning at [Start time] on [Date] in order to set up the appropriate stations, goods, or other items necessary in order to complete the services described. \nItems that require physical display space must be no larger than [Dimensions] and shall be displayed in a clean and orderly fashion throughout the course of the Event. No goods or services not described above may be sold or distributed during this Event without the Client’s express written consent.\n Following the event, the Vendor will have until [End time] to break down all equipment and clear the area of all goods. The Vendor is required to leave the area in a clean and serviceable manner.",
        appearance:
          "The Vendor will display an appearance and manner appropriate with the mood and theme of the Event being held. The vending station will not in any way interfere with the Event on hand, nor will vending staff leave the station unattended. Any special dress or appearance requirements outside of the accepted norm will be discussed in advance between the Client and the Vendor.\nBy signing below, both the Client and the Vendor indicate that they have read, understand, and agree to all terms and conditions outlined in this contract.",
        comments: "We should rethink the compensation fees.",
        comment_response:
          "The proposed compensation fee is adequate for this client."
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
