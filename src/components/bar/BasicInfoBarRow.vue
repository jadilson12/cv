<template>
    <v-container class="about-page">
        <!-- Avatar -->
        <v-container class="pt-0 pb-0">
            <v-layout row>
                <v-flex text-center>
                    <v-avatar size="200px">
                        <img src="https://avatars2.githubusercontent.com/u/36805474" alt="">
                    </v-avatar>
                </v-flex>
                <!-- Basic Info -->
                <v-flex>
                    <v-container pt-4>
                        <info-text
                                v-for="item in basic"
                                :key="item.title"
                                :title="item.title"
                                :content="item.content"
                        ></info-text>
                    </v-container>
                </v-flex>
            </v-layout>
        </v-container>
    </v-container>
</template>

<script>
    import InfoText from "../../components/txt/InfoText";
    import { profile } from  '../../api/data'
    export default {
        name: "basic-info-bar-row",
        data() {
            return {
                basic: profile.basic,
                additional:profile.additional
            };
        },
        components: {
            InfoText
        }
    };
</script>
