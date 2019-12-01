<template>
    <v-container text-xs-left class="education-page width-limit-500">
        <h3 class="head">Graduação</h3>
        <formacao-text v-for="item in gaduacao" :key="item.title" :content="item"></formacao-text>
        <v-container class="divider-container" pa-0 pt-3 pb-3>
            <v-divider></v-divider>
        </v-container>
        <h3 class="head">Certificação</h3>
        <formacao-text v-for="item in certificacao" :key="item.title" :content="item"></formacao-text>
    </v-container>
</template>

<script>
import FormacaoText from "../components/txt/FormacaoText"
import { education } from '../api/data.json'
export default {
    name: "education",
    components: { FormacaoText},
    data() {
        return {
            gaduacao: education.gaduacao,
            certificacao: education.certificacao
        };
    },
};
</script>
<style>
    .education-page {
        padding-top: 0;
        padding-bottom: 0;
    }
</style>
