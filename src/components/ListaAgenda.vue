<template>
    <v-container>
        <v-card class="mx-auto w-50" theme="dark">
            <v-table theme="light" class="ma-5" density="compact">
                <thead>
                <tr>
                    <th class="text-left"> Nome </th>
                    <th class="text-left"> Telefone </th>
                    <th class="text-left"> Endereço </th>
                    <th class="text-left"> Telefone </th>
                </tr>
                </thead>
                <tbody>
                <tr v-for="contato in contatos" :key="contato.telefone">
                    <td>{{ contato.name }}</td>
                    <td>{{ contato.calories }}</td>
                    <td>{{ contato.name }}</td>
                    <td>{{ contato.calories }}</td>
                    <td>
                        <v-btn color="red">
                            Excluir
                        </v-btn>
                    </td>
                </tr>
                </tbody>
            </v-table>
        </v-card>
    </v-container>
</template>

<script>
export default {
  name: 'App',

  data(){
    return{

    }
  },
  props:{
    contatos:Object
  },
  components:{

  },
  methods:{

  }
}
</script>