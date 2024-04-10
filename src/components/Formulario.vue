<template>
    <v-container>
        <v-card class="mx-auto w-25" theme="dark">
            <form class="ma-5" fast-fail>
                <v-text-field  v-model="nome" :counter="10" label="Nome" ></v-text-field>
                <v-text-field  v-model="email" :counter="7" label="E-mail" ></v-text-field>
                <v-text-field  v-model="endereco" label="Endereço" ></v-text-field>
                <v-text-field  v-model="telefone" type="number" label="Telefone" ></v-text-field>
                <v-btn class="me-4" color="success" :disabled="editar == true" @click="Cadastrar()">
                    Adicionar
                </v-btn>
                <v-btn class="me-4" color="warning" :contatos="contatos" type="submit"  :disabled="editar == false" @click="ConfirmarEdit()">
                    Editar
                </v-btn>
            </form>
        </v-card>
        <v-divider class="ma-5"></v-divider>
        <v-card class="mx-auto w-75" theme="dark">
            <v-table theme="light" class="ma-5">
                <thead>
                <tr>
                    <th class="text-left"> ID </th>
                    <th class="text-left"> Nome </th>
                    <th class="text-left"> E-mail </th>
                    <th class="text-left"> Endereço </th>
                    <th class="text-left"> Telefone </th>
                    <th class="text-left"> Ação </th>
                </tr>
                </thead>
                <tbody>
                <tr v-for="contato in contatos" :key="contato.telefone">
                    <td>{{ contato[0] }}</td>
                    <td>{{ contato[1] }}</td>
                    <td>{{ contato[2] }}</td>
                    <td>{{ contato[3] }}</td>
                    <td>{{ contato[4] }}</td>
                    <td>
                        <v-btn color="red" @click="Deletar(contato[0])">
                            Excluir
                        </v-btn>
                        <v-btn color="warning   " @click="Editar(contato[0],contato[1],contato[2],contato[3],contato[4])">
                            Editar
                        </v-btn>
                    </td>
                </tr>
                </tbody>
            </v-table>
        </v-card>
    </v-container>
</template>

<script>
//import ListaAgenda from '@/components/ListaAgenda.vue';
export default {
  name: 'App',

  data(){
    return{
        contErros:0,
        editar:false,
        index:1,
        ultimoIndex: 1,
        nome: "",
        email: "",
        endereco: "",
        telefone: 0,
        contatos:[],        
    }
  },
  components:{
    //ListaAgenda
  },
  methods:{
    Cadastrar(){
        if(this.contErros == 0){
            let contato = [this.index,this.nome,this.email,this.endereco,this.telefone]
            this.contatos.push(contato)
            console.log(this.contatos)
            this.index++
            this.Resetar()
            this.ultimoIndex = this.index            
        }else{
            alert("Ajuste os campos e tente novamente")
        }

    },
    Resetar(){
        this.nome = "",
        this.endereco = "",
        this.email = "",
        this.telefone = 0
    },
    Deletar(id_contato){
        this.contatos.splice(id_contato-1,1);
    },
    Editar(id_contato,nome,email,endereco,telefone){
        this.editar = true
        this.index = id_contato,
        this.nome = nome,
        this.email = email,
        this.endereco = endereco,
        this.telefone = telefone
    },
    ConfirmarEdit(){
        let contatoEditado = [this.index,this.nome,this.email,this.endereco,this.telefone]
        let indice = this.contatos.findIndex(objeto => objeto.id === contatoEditado.id);

        if (indice !== -1) {
            this.contatos[indice] = contatoEditado;
        }

        this.nome,this.email,this.endereco = "";
        this.telefone = 0;
        this.editar = false;
        this.index = this.ultimoIndex;
    }
  }
}
</script>