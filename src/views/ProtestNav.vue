<template>
  <div>
  <b-row>
  <b-col></b-col>
  <b-col cols="10">
    <br>
    <h1>Protestas</h1>
    <div v-for="post in posts" :key="post.title">
      <b-card>
        <h4>{{post.title}}</h4><br>
        Ubicación: {{post.location}}
      </b-card>
    </div>
  </b-col>
  <b-col></b-col>
  </b-row>
  </div>
</template>

<script>
export default {
  name: "LeafletMap",
  data() {
    return {
      posts: [
        {
          title: '#NoMasAFP',
          location: 'Universidad de Concepción, Concepción, Chile'
        },
        {
          title: '#LaMarchaMasGrandeDeChile',
          location: 'Plaza Italia, Santiago, Chile'
        },
        {
          title: '#NoMasTag',
          location: 'Plaza Ñuñoa, Santiago, Chile'
        },
      ]
    };
  }
}
</script>