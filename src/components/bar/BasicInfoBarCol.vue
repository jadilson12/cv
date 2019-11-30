<template>
    <v-container class="about-page">
        <v-layout>
            <!-- Avatar -->
            <v-flex>
                <v-avatar size="200px">
                    <img src="https://avatars2.githubusercontent.com/u/36805474" alt="">
                </v-avatar>
            </v-flex>
            <!-- Text Info -->
            <v-container>
                <v-layout column>
                    <!-- Basic Info -->
                    <v-flex>
                        <info-text
                                v-for="item in basic"
                                :key="item.title"
                                :title="item.title"
                                :content="item.content"
                        ></info-text>
                    </v-flex>
                    <!-- Additional Info -->
                    <v-flex>
                        <info-text
                                v-for="item in additional"
                                :key="item.title"
                                :title="item.title"
                                :content="item.content"
                        ></info-text>
                    </v-flex>
                </v-layout>
            </v-container>
        </v-layout>
    </v-container>
</template>

<script>
    import InfoText from "../../components/txt/InfoText";
    import { profile } from  '../../api/data'
    export default {
        name: "basic-info-bar-col",
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
