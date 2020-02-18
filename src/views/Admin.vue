<template>
  <div>
    <navBar />
    <v-content>
      <v-container class="fill-height" fluid>
        <v-row align="center" justify="center">
          <v-col cols="12" sm="8" md="12">
            <v-card class="elevation-12" height=auto>
                <v-card-title>
                   Table
                    <v-spacer />
                    <v-col md="3">
                      <v-text-field
                        v-model="search"
                        label="Search"
                        solo
                        filled
                        rounded
                        hide-details
                        dense
                        clearable
                        flat
                        prepend-inner-icon="mdi-magnify"
                      ></v-text-field>
                    </v-col>
                  </v-card-title>
                  <v-data-table
                    :headers="headers"
                    :items="items"
                    class="elevation-1"
                    :search="search"
                    fixed-header
                    height="380px"
                  >
                   </v-data-table>
              </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </div>
</template>

<script>
import navBar from '../components/navBar.vue'
export default {
  data: () => ({
    search: '',
    headers: [
      {
        text: 'Item Name',
        align: 'left',
        value: 'name'
      },
      { text: 'Actions', align: 'right', value: 'action', sortable: false }
    ]
  }),
  components: {
    navBar
  },
  mounted () {
    if (localStorage.getItem('pageDetails') === 'admin') {
    } else if (localStorage.getItem('pageDetails')) {
      var pageAuth = localStorage.getItem('pageDetails')
      this.$router.replace({ name: pageAuth })
    } else {
      this.$router.replace({ name: 'login' })
      localStorage.clear()
    }
  }
}
</script>
