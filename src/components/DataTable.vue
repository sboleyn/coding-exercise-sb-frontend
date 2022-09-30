<template>
  <v-container>
    <v-data-table
      :headers="headers"
      :items="info"
      :footer-props="{
        'items-per-page-options': [50, 100, 1000],
      }"
      :items-per-page="50"
      class="elevation-1"
    ></v-data-table>
  </v-container>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      url: "https://cors-anywhere.herokuapp.com/https://coding-exercise-sb.herokuapp.com/api/us/covid-19/levels-by-county/?format=json",
      headers: [
        {
          text: "County",
          align: "start",
          sortable: true,
          value: "county",
        },
        { text: "County FIPS", value: "county_fips" },
        { text: "State", value: "state" },
        { text: "County Population", value: "county_population" },
        {
          text: "Health Service Area Number",
          value: "health_service_area_number",
        },
        { text: "Health Service area", value: "health_service_area" },
        {
          text: "Health Service Area Population",
          value: "health_service_area_population",
        },
        {
          text: "Inpatient Bed Utilization",
          value: "covid_inpatient_bed_utilization",
        },
        {
          text: "Hospital Admissions per 100k",
          value: "covid_hospital_admissions_per_100k",
        },
        { text: "Cases per 100k", value: "covid_cases_per_100k" },
        { text: "Community Levels", value: "covid19_community_level" },
        { text: "Date Updated", value: "date_updated" },
      ],
      info: [],
    };
  },
  mounted() {
    // axios.get(this.url).then((response) => {
    //   this.info = response.data.results;
    // });
    this.getData();
  },
  methods: {
    getData() {
      axios
        .get(this.url, {
          headers: {
            Accept: "application/json",
            "Content-Type": "application/json",
          },
        })
        .then((response) => {
          this.info = response.data.results;
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>