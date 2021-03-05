<template>
  <div>
    <body background="">
      <b-row>
       <center><img
          src="https://defaeroreport.com/wp-content/uploads/2019/07/nasa-logo-web-rgb.png"
          alt=""
          height="120"
          width="200"
        /></center> 

        <h1 class="text-dark">NASA AXIOS</h1></b-row
      >
      <div class="container">
        <br /><br />
        <b-row>
          <b-card
            v-for="user in userList"
            :key="user.results"
            title=""
            img-src="https://www.kindpng.com/picc/m/42-424822_black-and-white-nasa-logo-hd-png-download.png"
            img-alt=""
            img-top
            tag="article"
            style="max-width: 20rem;"
            class="mb-2"
            color="drack"
          >
            ID : {{ user.activityID }}<br /><br />
            {{ user.catalog }}<br /><br />
            Time: {{ user.startTime }}<br /><br />
            {{ user.note }}
            <a :href="user.link"
              ><br /><br /><button type="button" class="btn btn-outline-dark">
                More
              </button></a
            >
          </b-card>
        </b-row>
      </div>
    </body>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      userList: null,
    };
  },
  mounted() {
    let url =
      "https://api.nasa.gov/DONKI/CME?startDate=yyyy-MM-dd&endDate=yyyy-MM-dd&api_key=DEMO_KEY";
    axios
      .get(url)
      .then((response) => {
        this.userList = response.data;
      })
      .catch();
    (err) => {
      console.log(err);
    };
  },
};
</script>
