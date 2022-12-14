<template>
  <section> 
    <Cabecalho :titulo="titulo" />
    <div class="container">
      <div class="holder">
        <h2>Minha Lista de Tarefas</h2>
        <div class="input-group">
          <input type="text" v-model="novaTarefa" @keydown.enter="adicionarTarefa">
          <span class="input-group-btn">
            <button @click="adicionarTarefa" class="btn btn-primary">Adicionar Tarefa</button>
          </span>
        </div>
        <ListaTarefas @excluir="excluir" :tarefas="tarefas"/>
      </div>
    </div>
    <Rodape />
  </section>
  
</template>

<script>
import Cabecalho from "./components/Cabecalho.vue";
import ListaTarefas from "./components/ListarTarefas.vue"
export default {
  name: 'App',
  components: {Cabecalho, ListaTarefas},
  data() {
    return{
      titulo: "Minha Lista de Tarefas",
      novaTarefa: "",
      tarefas: [
        {titulo: "Estudar", checked: false},
        {titulo: "Programar", checked: true}
      ],
    }
  },
  methods: {
    adicionarTarefa() {
      if(this.novaTarefa !== ""){
        this.tarefas.push({
        titulo: this.novaTarefa,
        checked: false,
      });
        this.novaTarefa = "";
      }
    },
    excluir(index){
      this.tarefas.splice(index,1)
    }
  }
}
</script>

<style>
.container{
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 40%;
  margin: 300px auto 0px auto;
}

ul li{
  list-style: none;
}
.holder{
  padding: 50px;
  background-color: royalblue;
  color: rgb(206, 199, 199);
  border-radius: 20px;
}
.removed{
  color:gray;
}
.removed label{
  text-decoration: line-through;}
</style>
