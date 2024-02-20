<template>
    <div class="pa-auto ma-auto">
        <v-alert v-if="alert" type="success" title="Cadastro Realizado" dismissible @click:close="alert = false">
            Cadastro Realizado
        </v-alert>

        <v-container>
            <v-responsive class="align-center pa-16">
                <v-form class="d-flex align-self-auto justify-center">
                    <v-row class="px-14">
                        <v-col cols="12">
                            <h3 class="align">Nome:</h3>
                            <v-text-field placeholder="Ex: Ana"></v-text-field>
                        </v-col>
                        <v-col cols="12">
                            <h3 class="align">Sobrenome:</h3>
                            <v-text-field placeholder="Ex: Maria da silva"></v-text-field>
                        </v-col>
                        <v-col cols="6">
                            <h3 class="align">E-mail:</h3>
                            <v-text-field placeholder="Ex: maria.silva.iplace@icloud.com"></v-text-field>
                        </v-col>
                        <v-col cols="6">
                            <h3 class="align">DDD + Telefone:</h3>
                            <v-text-field placeholder="Ex: 0119123456768"></v-text-field>
                        </v-col>
                        <v-col cols="6">
                            <h3 class="align">Cidade:</h3>
                            <v-text-field placeholder="Ex: São Paulo"></v-text-field>
                        </v-col>
                        <v-col cols="6">
                            <h3 class="align">Estado:</h3>
                            <v-combobox
                                :items="['California', 'Colorado', 'Florida', 'Georgia', 'Texas', 'Wyoming']"></v-combobox>
                        </v-col>
                        <v-col cols="12">
                            <h2 class="mb-3">Quais ofertas você gostaria de receber?</h2>
                            <hr>
                        </v-col>
                        <v-col v-for="logo in logos" :key="logo.id" cols="3">
                            <div :style="{ border: logo.borderStyle }" class="position-relative">
                                <v-card>
                                    <v-img height="auto" src="@/assets/logo.svg" />
                                </v-card>
                                <input type="checkbox" v-model="logo.isChecked" @click="toggleBorder(logo)"
                                    class="checkbox">
                            </div>
                        </v-col>

                        <v-col cols="4">
                            <v-btn @click="limpar" class="w-100 py-8 d-flex justify-center" size="x-large"
                                variant="outlined" rounded="lg" dark>limpar dados</v-btn>
                        </v-col>
                        <v-col cols="8">
                            <v-btn class="w-100 py-8 d-flex justify-center" size="x-large" variant="elevated" rounded="lg"
                                @click="salvar" color="black" dark>Confirmar Cadastro</v-btn>
                        </v-col>
                    </v-row>
                </v-form>
            </v-responsive>
        </v-container>
    </div>
</template>

<script>
export default {
    data() {
        return {
            logos: [
                { id: 1, isChecked: false, borderStyle: '2px solid black' },
                { id: 2, isChecked: false, borderStyle: '2px solid black' },
                { id: 3, isChecked: false, borderStyle: '2px solid black' },
                { id: 4, isChecked: false, borderStyle: '2px solid black' }
            ],
            alert: false
        };
    },
    methods: {
        toggleBorder(logo) {
            logo.borderStyle = !logo.isChecked ? '2px solid green' : '2px solid black';
        },
        limpar() {
            this.logos.forEach(logo => {
                logo.isChecked = false;
                logo.borderStyle = '2px solid black';
            });
        },
        salvar() {
            this.alert = true;
            setTimeout(() => {
                this.alert = false;
            }, 3000);
        }
    }
};
</script>

<style scoped>
.checkbox {
    position: absolute;
    top: 5px;
    right: 5px;
    z-index: 1;
}
</style>