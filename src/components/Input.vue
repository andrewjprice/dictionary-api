<template>
  <div class="container">
    <div class="field">
      <input @keyup.enter="onSubmit($event)">
    </div>
    <div class="display">
      <p class="definition">{{definition}}</p>
      <p>{{error}}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Input',
  data: function() {
    return {
        definition: null,
        error: null
      }
    },
  methods: {
    onSubmit: function(e) {
      var word = e.target.value
      var key = process.env.VUE_APP_API_KEY
      var url = process.env.VUE_APP_BASE_URL

      axios
        .get(`${url}${word}?key=${key}`)
        .then(response => {
          var data = response.data
          this.definition = data[0].shortdef[0]
        })
        .catch(error => {
          this.error = error
        });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.field {
  display: flex;
  justify-content: center;
}
.display {
  display: flex;
  justify-content: center;
}

.definition {
  color: white;
}
</style>
