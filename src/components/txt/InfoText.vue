<template>
    <v-container pa-0>
        <v-layout row>
            <v-flex class="pr-2 pt-0 xs6" text-right>
                <h3  v-text="title"></h3>
            </v-flex>
            <v-flex xs6 text-left>
                <p class="pt-1" v-text="content"></p>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
export default {
    name: "info-text",
    props: ["title", "content"]
};
</script>
