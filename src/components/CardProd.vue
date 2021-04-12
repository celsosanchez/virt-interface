<template>
  <v-app id="inspire">
    <v-main>
      <v-container class="py-8 px-6" fluid>
        <v-row class="text-center" >
          <v-card>
            <v-list two-line>
              <template v-for="n in products">
                <v-list-item :key="products.indexOf(n)">
                  <v-list-item-avatar color="grey darken-1">
                      <v-img :src="n.image_small_url"></v-img>
                  </v-list-item-avatar>

                  <v-list-item-content>
                    <v-list-item-title
                      >{{ n.product_name }}            <app-date :timestamp="new Date(n.production_datetime).getTime()"/>   </v-list-item-title
                    >

                    <v-list-item-subtitle>
                      Lorem ipsum dolor sit amet, consectetur adipisicing elit.
                      Nihil repellendus distinctio similique
                    </v-list-item-subtitle>
                  </v-list-item-content>
                </v-list-item>

                <v-divider
                  v-if="n !== 6"
                  :key="`divider-${n}`"
                  inset
                ></v-divider>
              </template>
            </v-list>
          </v-card>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import AppDate from './AppDate.vue';
export default {
    components:{
        AppDate
        
    },
  props: {
    products: {
      required: true,
    },
  },
  data: () => ({}),
};
</script>
