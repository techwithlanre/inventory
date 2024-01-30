<template>
    <div class="flex flex-row min-h-screen">
        <div class="w-2/12 bg-[#F9F9F9] p-10">
            <ul>
                <li v-for="link in links" class="mb-3">
                    <nuxt-link :to="link.route" class="font-semibold">{{ link.title }}</nuxt-link>
                </li>
            </ul>
        </div>
        <div class="w-10/12 p-10">
            <h1 class="font-bold text-lg mb-10">Products List</h1>
            <slot />
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            links: [
                {
                    'title': "Products",
                    'route': '/' 
                },
                {
                    'title': "Purchases",
                    'route': '/purchases' 
                },
                {
                    'title': "Sales",
                    'route': '/sales' 
                },
            ]
        }
    }
}
</script>