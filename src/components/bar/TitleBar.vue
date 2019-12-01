<template>
  <v-container flat class="title pt-0 mt-0" text-center>
    <v-flex id="small">
      <v-menu offset-y>
        <template v-slot:activator="{ on }">
          <v-btn v-on="on" class="transparent" v-text="menuStart"> </v-btn>
        </template>
        <v-list>
          <v-list-item v-for="item in menu" :key="item.title" @click="select(item)">
            <v-list-item-title class="mr-2" v-text="item.title"></v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-flex>
    <v-flex id="full">
      <v-btn-toggle v-model="selected" class="menu-full" borderless mandatory>
        <v-btn v-for="(item, i) of menu" :key="i" v-text="item.title" class="menu-title"></v-btn>
      </v-btn-toggle>
    </v-flex>
  </v-container>
</template>

<script>
  import {menu} from '../../api/data'
    export default {
        name: "title-bar",
        data: () => ({
            screenSize: false,
            selected: 0,
            menuStart: "Sobre",
            menu: menu
        }),
        watch: {
            selected() {
                this.menuStart = this.menu[this.selected].title;
                this.$emit("changePage", this.selected);
            }
        },
        methods: {
            select(item) {
                this.selected = item.number;
                this.menuStart = ` ${item.title}`;
            },
        }
    };
</script>


<style>

  .menu-full {
    background: transparent none !important;
  }
  .menu-title{

  }
  .theme--light.v-btn:not(.v-btn--flat):not(.v-btn--text):not(.v-btn--outlined) {
    background-color: transparent;
  }

  @media (min-width: 697px) {
    #full {
      display: block;
    }

    #small {
      display: none;
    }
  }

  @media (min-width: 0px) and (max-width: 695px) {
    #full {
      display: none;
    }

    #small {
      display: block;
    }
  }

  .v-btn-toggle--selected {
    box-shadow: none;
  }

  .v-btn__content {
    font-size: 16px;
  }

  .btn--active .v-btn__content:before,
  .btn:focus .v-btn__content:before,
  .btn:hover .v-btn__content:before {
    background-color: initial;
    outline: black;
  }

  .title {
    padding: 0;
    margin: 0 auto;
  }

  .v-btn-toggle:not(.v-btn-toggle--dense) .v-btn.v-btn.v-size--default {
    height: 30px !important;
    font-weight: 300 ;
    box-shadow: initial;

  }

  .v-btn-toggle > .v-btn.v-btn{
    border-radius: unset !important;
  }

</style>
