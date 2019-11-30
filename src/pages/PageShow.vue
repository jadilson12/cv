<template>
    <v-container flat grid class="page">
        <transition name="fade" mode="out-in">
            <formacao-page v-if="pressed==='formacao'"></formacao-page>
        </transition>
    </v-container>
</template>

<script>
    import FormacaoPage from "./FormacaoPage";

    export default {
        name: "page-show",
        props: ["pressed"],
        components: {
            FormacaoPage
        }
    };
</script>

<style>
    .page {
        padding: 0;
    }
    /* Transitions */
    .fade-enter-active {
        transition: opacity 0.5s;
    }
    .fade-leave-active {
        transition: opacity 0.1s;
    }
    .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
        opacity: 0;
    }
    .fade-enter-to,
    .fade-leave {
        opacity: 1;
    }
</style>
