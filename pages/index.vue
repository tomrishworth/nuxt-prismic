<template>
  <section class="container">
    <div>
        {{ homepage }}
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      homepage: []
    };
  },
  asyncData(context) {

    var Prismic = require("prismic-javascript");

    var apiEndpoint = "https://rpr-pacific.cdn.prismic.io/api/v2";
    var apiToken = "MC5XdFczVnlZQUFOdXVjdmxi.77-977-977-977-9AGjvv73vv73vv73vv73vv73vv71g77-9BHDvv71PXDVJ77-977-977-977-9B--_ve-_ve-_vQkbWg";

    Prismic.getApi(apiEndpoint, {accessToken: apiToken})
      .then(function(api) {
        console.log('Here')
        return api.query(
          Prismic.Predicates.at('document.id', 'WtUCqiYAAHGib_sY')
        );
      })
      .then(
        function(response) {
          console.log(response.results);
          return {
            homepage: response
          };
        },
        function(err) {
          console.log("Something went wrong: ", err);
        });
  },
  mounted() {
    console.log("Mounted");
  }
};
</script>

