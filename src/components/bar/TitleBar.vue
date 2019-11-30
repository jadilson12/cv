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
                    <v-list-item v-for="item in menuItems" :key="item.title"   @click="select(item)">
                      <v-list-item-title class="mr-2">{{ item.title }}</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-menu>
        </v-flex>
        <v-flex id="full">
            <v-btn-toggle  v-model="selected" class="menu-full" borderless mandatory>
                <v-btn >Sobre</v-btn>
                <v-btn >Habilidades</v-btn>
                <v-btn >Esperiêcias</v-btn>
                <v-btn >Formação</v-btn>
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
        }
    };
</script>

<style>
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
    .theme--light .v-btn-toggle {
      background: none;
    }
    .v-btn-toggle--selected {
      box-shadow: none;
    }
    .v-btn__content {
      font-weight: 300;
      font-size: 20px;
    }
    .btn--active .v-btn__content:before,
    .btn:focus .v-btn__content:before,
    .btn:hover .v-btn__content:before {
      background-color: initial;
      outline: black;
    }
    .title {
      padding: 0;
      margin: 0;
    }
</style>
