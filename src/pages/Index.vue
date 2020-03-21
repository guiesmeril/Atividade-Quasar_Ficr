<template>
  <q-page class="container">
<q-card flat bordered class="my-card col-md-3 col-sm-4" v-for="personagem in personagens" :key="personagem.name" style="background: radial-gradient(circle, #35a2ff 0%, #014a88 100%)">
      <q-card-section>
        <div class="text-h6 row q-col-gutter-sm">{{ personagem.name }}</div>
      </q-card-section>
      <q-card-section class="q-pt-none">
        Gender: {{ personagem.gender }}<br>
        Height: {{ personagem.height }}<br>
        Hair_color: {{ personagem.hair_color }}<br>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      personagens: []
    }
  },
  methods: {
    carregarPersonagens () {
      this.$axios.get('https://swapi.co/api/people/?page=1').then(response => {
        this.personagens = (response.data.results)
      })
    }
  },
  beforeMount () {
    this.carregarPersonagens()
  }
}
</script>
