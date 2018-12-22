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
      var key = process.env.API_KEY
      var url = process.env.BASE_URL

      axios
        .get(`https://www.dictionaryapi.com/api/v3/references/collegiate/json/${word}?key=99779dfc-7950-4dc8-ab30-d75b13efd5ae`)
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
