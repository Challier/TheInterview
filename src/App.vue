<template>
  <v-app>
    <v-navigation-drawer v-model="sideNav" temporary>
        <v-list>
          <v-list-tile>
            <v-list-tile-action>
              <v-icon>plus_one</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>Add Question</v-list-tile-content>
          </v-list-tile>
        </v-list>
    </v-navigation-drawer>
    <v-toolbar dark class="green accent-4" flat>
      <v-toolbar-side-icon 
        @click.native.stop="sideNav = !sideNav"
        class="hidden-sm-and-up">
      </v-toolbar-side-icon>
      <v-toolbar-title>Tech Interviews</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items
        class="hidden-xs-only">
        <v-dialog v-model="dialog" temporary>
          <v-btn flat slot="activator"><v-icon left>plus_one</v-icon>Add Question</v-btn>
          <v-card>
            <v-card-title>
              <span class="headline">Add Question</span>
            </v-card-title>
            <v-card-text>
              <v-select
                label="Company"
                required
                :items="['Amazon', 'Facebook', 'Google', 'Uber']"
              ></v-select>
              <v-select
                label="Category"
                required
                :items="['Behavior', 'Business', 'Coding', 'Logic']"
              ></v-select>
              <v-text-field
                label="Question" 
                multi-line 
                required
              ></v-text-field>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn class="blue--text darken-1" flat @click.native.stop="dialog = false">Close</v-btn>
              <v-btn class="blue--text darken-1" flat @click.native="dialog = false">Send</v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-toolbar-items>
    </v-toolbar>
    
    <main>
    <router-view></router-view>
    </main>
  </v-app>
</template>

<script>
  export default {
    data () {
      return {
        sideNav: false,
        dialog: true
      }
    }
  }
</script>

<style lang="stylus">
  @import './stylus/main'
</style>
