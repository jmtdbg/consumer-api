<template>
    <v-card class="py-2">
        <v-card-title primary-title>
            <v-btn color="primary" small :to="`/`">
                <v-icon>fas fa-arrow-left</v-icon>
            </v-btn>
        </v-card-title>
        <v-card class="py-4 px-4 mx-3 my-2">
            <v-card-title> Residência {{ residencias.id }} </v-card-title>
            <v-divider></v-divider>
            <v-card-text class="my-2">
                <!-- <v-row v-for="(chave, index) in Object.keys(residencias)" :key="index">
                    {{chave}}: {{residencias[chave]}}
                    </v-row> -->
                <v-simple-table>
                    <tbody>
                        <tr v-for="(chave, index) in Object.keys(residencias)" :key="index">
                            <td>{{ chave }}:</td>
                            <td>{{ residencias[chave] }}</td>
                        </tr>
                    </tbody>
                </v-simple-table>
            </v-card-text>
        </v-card>
    </v-card>
</template>

<script>
export default {
    async mounted() {
        const response = await this.axios.get(
            `http://127.0.0.1:5000/residencias/${this.$route.params.id}`
        );
        console.log(response);
        this.residencias = response.data;
    },
    data() {
        return {
            residencias: [],
        };
    },
};
</script>