<template>
    <NuxtLayout title="Products List">
        <div class="relative overflow-x-auto">
            <table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
                <thead  class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                    <tr>
                        <th scope="col" class="px-6 py-3">Name</th>
                        <th scope="col" class="px-6 py-3">Quantity</th>
                        <th scope="col" class="px-6 py-3">Cost Price</th>
                        <th scope="col" class="px-6 py-3">Selling Price</th>
                    </tr>
                </thead>
                <tbody >
                    <tr v-if="currentlyFetching == false" v-for="product in products">
                        <td class="px-6 py-4">{{ product.name }}</td>
                        <td class="px-6 py-4">{{ product.quantity }}</td>
                        <td class="px-6 py-4">${{ product.cost_price }}</td>
                        <td class="px-6 py-4">${{ product.selling_price }}</td>
                    </tr>
                    <tr v-else>
                        <td class="text-center py-5" colspan="4">Fetching products ........</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </NuxtLayout>
</template>
<script>
export default {
    data() {
        return {
            baseUrl: "https://65b8b1ebb71048505a893847.mockapi.io",
            products: [],
            currentlyFetching: false
        }
    },
    methods: {
        async getProducts() {
            this.currentlyFetching = true;
            const endPoint = '/products';
            await $fetch(this.baseUrl + endPoint).then((response) => {
                this.products = response;
                console.log(this.products);
                this.currentlyFetching = false;
            });
        }
    },

    mounted() {
        this.getProducts();
    }
}
</script>