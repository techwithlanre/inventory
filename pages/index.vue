<template>
    <div class="relative overflow-x-auto">
        <table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
            <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                <tr>
                    <th scope="col" class="px-6 py-3">Name</th>
                    <th scope="col" class="px-6 py-3">Quantity</th>
                    <th scope="col" class="px-6 py-3">Cost Price</th>
                    <th scope="col" class="px-6 py-3">Selling Price</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="product in products">
                    <td class="px-6 py-4">{{ product.name }}</td>
                    <td class="px-6 py-4">{{ product.quantity }}</td>
                    <td class="px-6 py-4">${{ product.cost_price }}</td>
                    <td class="px-6 py-4">${{ product.selling_price }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script>
export default {
    data() {
        return {
            baseUrl: "https://65b8b1ebb71048505a893847.mockapi.io",
            products: []
        }
    },
    methods: {
        async getProducts() {
            const endPoint = '/products';
            await $fetch(this.baseUrl + endPoint).then((response) => {
                this.products = response;
            });
        }
    },

    mounted() {
        this.getProducts();
    }
}
</script>