<script setup>
import { onMounted, ref } from 'vue'
import axios from 'axios'
import 'bootstrap/dist/css/bootstrap.min.css'

const loading = ref(true)

const array = ref([])

onMounted(async () => {
  for (let indice = 1; indice < 151; indice++) {
    try {
      const response = await axios.get('https://pokeapi.co/api/v2/pokemon/' + indice)
      const dados = response.data
      array.value.push(dados) // Adiciona os dados da API a variavel "array"
    } catch (error) {
      console.log('Falha ao receber os dados da API.')
    }
  }

  loading.value = false
})
</script>

<template>
  <div class="loading" v-if="loading">
    <img src="../assets/images/loading_pokeball.gif" alt="tela de carregamento" />
  </div>

  <main class="container" v-if="!loading">
    <div class="row">
      <div class="col-12 col-sm-6 col-md-4 col-lg-3" v-for="v in array" :key="v.id">
        <div class="card" :class="v.types[0].type.name">
          <img :src="v.sprites.other.home.front_default" />
          <p style="text-align: center">{{ v.name }}</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.loading {
  text-align: center;
}

.form-search {
  margin-top: 30px;
}
.card {
  margin-top: 1.875rem;
  transition: transform 0.4s;
}

.card p {
  font-size: 1.125rem;
  margin-top: 0.625rem;
}
.card:hover {
  transform: scale(1.1, 1.1);
}

.grass {
  background-color: rgb(92, 184, 92);
}

.fire {
  background-color: rgb(188, 89, 89);
}

.water {
  background-color: rgb(51, 58, 187);
}

.bug {
  background-color: rgb(165, 188, 89);
}

.normal {
  background-color: rgb(227, 227, 227);
}

.poison {
  background-color: rgb(93, 73, 167);
}

.ground {
  background-color: rgb(153, 122, 65);
}

.fairy {
  background-color: rgb(167, 94, 175);
}

.electric {
  background-color: rgb(245, 237, 86);
}

.fighting {
  background-color: rgb(174, 166, 118);
}

.psychic {
  background-color: rgb(130, 19, 182);
}

.rock {
  background-color: rgb(91, 83, 64);
}

.ghost {
  background-color: rgb(88, 74, 95);
}

.ice {
  background-color: rgb(24, 167, 195);
}

.dragon {
  background-color: rgb(236, 162, 0);
}

.dark {
  background-color: rgb(85, 85, 85);
}

.steel {
  background-color: rgb(119, 119, 119);
}
@media (max-width: 768px) {
  .loading img {
    width: 75%;
    margin-top: 6rem;
  }
}

@media (max-width: 576px) {
  .loading img {
    width: 50%;
    margin-top: 6rem;
  }
}
</style>
