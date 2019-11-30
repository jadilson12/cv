<template>
    <v-container flat class="title" text-center>
        <v-flex id="small">
            <v-menu offset-y>
                <template v-slot:activator="{ on }">
                    <v-btn v-on="on" class="transparent">
                      {{ menuName }}
                    </v-btn>
                </template>
                <v-list>
                    <v-list-item v-for="item in menuItems" :key="item.title"   @click="select(item)"
                    >
                      <v-list-item-title class="mr-2">{{ item.title }}</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-menu>
        </v-flex>
        <v-flex id="full" class="transparent">
            <v-btn-toggle flat v-model="selected" class="transparent" borderless mandatory>
                <v-btn class="mr-2" flat >Sobre</v-btn>
                <v-btn class="mr-2" flat>Habilidades</v-btn>
                <v-btn class="mr-2" flat>Esperiêcias</v-btn>
                <v-btn class="mr-2" flat>Formação</v-btn>
            </v-btn-toggle>
        </v-flex>
    </v-container>
</template>

<script>
    export default {
        name: "title-bar",
        data: () => ({
          screenSize: false,
          selected: 0,
          menuName: "Sobre",
          menuItems: [
            {
              title: "Sobre",
              number: 0
            },
            {
              title: "Habilidades",
              number: 1
            },
            {
              title: "Esperiêcias",
              number: 2
            },
            {
              title: "Formação",
              number: 3
            }
          ]
        }),
        watch: {
            selected() {
                this.menuName = this.menuItems[this.selected].title;
                this.$emit("changePage", this.selected);
            }
        },
        methods: {
            select(item) {
                this.selected = item.number;
                this.menuName = ` ${item.title}`;
            },
            onSmallScreen() {
                if (window.innerWidth > 1000) {
                    this.screenSize = false;
                } else {
                    this.screenSize = true;
                }
            }
        }
    };
</script>

<style>
    /* Media Queries */
    @media (min-width: 651px) {
        #full {
            display: block;
        }

        #small {
            display: none;
        }
    }

    @media (min-width: 0px) and (max-width: 650px) {
        #full {
            display: none;
        }

        #small {
            display: block;
        }
    }

    /* Button Restyling */
    .theme--light .btn-toggle {
        background: none;
    }

    .btn-toggle--selected {
        box-shadow: none;
    }

    .btn__content {
        font-weight: 300;
        font-size: 20px;
    }

    .btn--active .btn__content:before,
    .btn:focus .btn__content:before,
    .btn:hover .btn__content:before {
        background-color: none;
        outline: black;
    }

    .title {
        padding: 0;
        margin: 0;
    }
</style>
