<template>
    <v-app-bar>
        <v-toolbar-title @click="$router.push('/')" style="cursor: pointer;">
            Shopping Website
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn @click="$router.push('/Cart')" class="text-none" stacked>
        <v-badge :content="cartStore.productCount" color="error">
            <v-icon>mdi-cart-outline</v-icon>
        </v-badge>
    </v-btn> 
    <v-btn
    :prepend-icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'"
    @click="cartStore.toggleTheme()">
    </v-btn>
    </v-app-bar>
</template>

<script setup>
import { useCartStore } from '../stores/cart';
const cartStore = useCartStore();
</script>

<style lang="scss" scoped>

</style>