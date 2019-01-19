<template>
<v-container grid-list-lg>
  <v-layout row class="mt-4">
    <v-flex xs6>
      <v-card>
        <v-list>
          <v-list-group
            v-for="(item, index) in items"
            v-model="item.active"
            :key="index"
            no-action
          >
            <v-list-tile slot="activator">
              <v-list-tile-content>
                <v-list-tile-title>{{ item.key }}</v-list-tile-title>
              </v-list-tile-content>
            </v-list-tile>

            <v-list-tile
              v-for="(subItem, index) in item.subjects"
              :key="index"
              @click=""
            >
              <v-list-tile-content>
                <v-list-tile-title
                    @click="setDescription(subItem)"
                >{{ subItem.name }}</v-list-tile-title>
              </v-list-tile-content>
            </v-list-tile>
          </v-list-group>
        </v-list>
      </v-card>
    </v-flex>
    <v-flex xs6>
      <v-card>
        <v-card-title>
            <b>{{ subItem.name }}</b>
        </v-card-title>
        <v-card-text>{{ subItem.description }}</v-card-text>
      </v-card>
    </v-flex>
  </v-layout>
</v-container>
</template>

<script>
import list from '../data/list.json'
  export default {
    mounted() {
        this.items = list;
    },
    methods: {
        setDescription(item) {
            this.subItem = item
        }
    },
    data () {
      return {
        items: [],
        subItem: {},
      }
    }
  }
</script>