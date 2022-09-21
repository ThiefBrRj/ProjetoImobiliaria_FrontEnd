<template>
    <v-container>
        <v-row class="text-center">
            <v-col cols="12">
                <template>
                    <v-data-table :headers="headers" :items="clientes" :items-per-page="10" class="elevation-1">
                    </v-data-table>
                </template>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
import axios from "axios";
export default {
    name: 'Cliente',

    data: () => ({
        headers: [
            { text: 'ID', value: 'id' },
            { text: 'Nome', value: 'nome' },
            { text: 'CPF', value: 'cpf' },
            { text: 'Telefone', value: 'telefone' },
            { text: 'Conta bancária', value: 'contaBancaria' },
        ],
        clientes: [],

    }),
    methods: {
        inicializa() {
            axios("http://localhost:3000/clientes")
                .then((response) => {
                    this.clientes = response.data
                })
                .catch((error) => console.log(error));
        }
    },
    created() {
        this.inicializa();
    }
}
</script>
