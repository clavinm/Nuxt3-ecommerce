<template>
  <div>
    <v-row class="my-5">
        <v-col cols="12">
            <v-btn :class="{'bg-primary': grid}" @click="grid = !grid">
                <v-icon>mdi-view-list</v-icon>
            </v-btn>
            <v-btn :class="{'bg-primary': !grid}" @click="grid = !grid" class="ml-3">
                <v-icon>mdi-apps</v-icon>
            </v-btn>
        </v-col>
    </v-row>
    <v-row>
        <v-col cols="12">
            <v-row v-show="grid">
                <v-col 
                    v-for="(product,i) in products"
                    :key="i"
                    cols="12"
                    lg="4"
                    sm="6">
                    <v-card class="mx-auto pb-2">
                        <v-img
                            height="200px"
                            :src="product.image"
                            alt="Card image"
                            cover
                        >
                        <template v-slot:placeholder>
                            <v-row class="fill-height ma-0" align="center" justify="center">
                                <v-progress-circular indeterminate color="grey lighten-5"></v-progress-circular>
                            </v-row>
                            <V-progress-circular indeterminate color="grey lighten-5"></V-progress-circular>
                        </template>
                    </v-img>
                        <v-card-title class="text-capitalize">{{ product.name }}</v-card-title>
                        <v-card-subtitle>{{ product.price }}</v-card-subtitle>
                        <v-card-text>{{ product.description }}</v-card-text>
                        <v-card-actions>
                            <v-btn color="primary">Read More</v-btn>
                            <v-spacer></v-spacer>
                            <v-btn class="bg-primary" @click="cartStore.add(product.id)">Add to Cart</v-btn>
                           
                        </v-card-actions>
                        </v-card>
                </v-col>

            </v-row>
            <v-row v-show="!grid" v-for="(product,i) in products" :key="i">
                <v-col cols="4">
                    <v-img
                            height="200px"
                            :src="product.image"
                            alt="Card image"
                            cover
                        >
                        <template v-slot:placeholder>
                            <v-row class="fill-height ma-0" align="center" justify="center">
                                <v-progress-circular indeterminate color="grey lighten-5"></v-progress-circular>
                            </v-row>
                            <V-progress-circular indeterminate color="grey lighten-5"></V-progress-circular>
                        </template>
                    </v-img> 
                </v-col>
                <v-col cols="12" md="8">
                    <v-card-title class="text-capitalize">{{ product.name }}</v-card-title>
                        <v-card-subtitle>{{ product.price }}</v-card-subtitle>
                        <v-card-text>{{ product.description }}</v-card-text>
                        <v-card-actions>
                            <v-btn color="primary">Read More</v-btn>
                            <v-spacer></v-spacer>
                            <v-btn class="bg-primary" @click="cartStore.add(product.id)">Add to Cart</v-btn>
                            
                        </v-card-actions>

                </v-col>

            </v-row>
        </v-col>
    </v-row>
  </div>
</template>

<script setup>
import { useCartStore } from '../stores/cart'
import data from '../data'
import { ref } from 'vue'

const cartStore = useCartStore();
const products = ref(data);
const grid = ref(true);
</script>

