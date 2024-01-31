<template>
    <NuxtLayout title="Add Product">
        <div class="mt-20 flex flex-row justify-center align-center max-w-3xl">
            <form action="" class="w-full" @submit.prevent="addProduct">
                <div class="flex flex-col gap-3">
                    <label for="">Name</label>
                    <input type="text" v-model="name" name="" id="" class="form-input">
                </div>
                <div class="flex flex-col gap-3 mt-5">
                    <label for="">Cost Price</label>
                    <input type="text" v-model="costPrice" name="" id="" class="form-input">
                </div>
                <div class="flex flex-col gap-3 mt-5">
                    <label for="">Selling Price</label>
                    <input type="text" v-model="sellingPrice" name="" id="" class="form-input">
                </div>
                <div class="flex flex-col gap-3 mt-5">
                    <label for="">Quantity</label>
                    <input type="text" v-model="quantity" name="" id="" class="form-input">
                </div>
                <div class="flex flex-col gap-3 mt-10">
                    <input v-if="currentlySubmitting == false" type="submit" name="" id="" class="btn">
                    <input v-else type="submit" name="" id="" class="busy-btn" value="Submitting.....">
                </div>
            </form>    
        </div>
    </NuxtLayout>
</template>

<style>
.form-input {
    @apply border p-3 rounded-lg
}

.btn {
    @apply bg-[#139a56] text-white px-5 py-3 rounded-lg hover:bg-red-500 duration-500
}

.busy-btn {
    @apply bg-[#139a56] text-white px-5 py-3 rounded-lg text-[#139a56] bg-opacity-10;
}
</style>

<script>
export default {
    data() {
        return {
            baseUrl: "https://65b8b1ebb71048505a893847.mockapi.io",
            name: "",
            costPrice: "",
            sellingPrice:"",
            quantity: "",
            currentlySubmitting: false
        }
    },

    methods: {
        async addProduct() {
            this.currentlySubmitting = true;
            await $fetch(this.baseUrl + "/products", {
                method: "POST", 
                body: {
                    name: this.name,
                    cost_price: this.costPrice,
                    selling_price: this.sellingPrice,
                    quantity: this.quantity,
                }
            }).then((response) => {
                console.log(response);
                this.clearFields();
                this.currentlySubmitting = false;
            })
        },

        clearFields() {
            this.name = "";
            this.costPrice = "";
            this.sellingPrice = "";
            this.quantity = "";
        } 
    }
}
</script>