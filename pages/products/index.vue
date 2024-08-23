<script setup lang="ts">
const {status, data: products} = await useFetch("https://fakestoreapi.com/products", {
    lazy: false
})

const url = '/products/'

</script>

<template>
    <div>
    <AppHeader />
    <UContainer>
        <main class="conatiner mx-auto p-4">
            <ContentDoc>
                <template v-slot="{ doc }">
                    <article>
                        <h1 class="text-2xl">{{ doc.title }}</h1>
                        <ContentRenderer :value="doc" />
                    </article>
                </template>
                <template #not-found>
                    <h1>Document not found</h1>
                </template>
            </ContentDoc>
           
            <h3 class="gap-4"><strong>Party product List</strong></h3>
            <div v-if="status === 'pending'">
            Loading ...
            </div>
           <div v-else class="grid grid-cols-5 gap-4">
            <div v-for="product in products"
            class="flex flex-col shadow-md bg-white p-6 rounded-md">
            <a :href="`/products/${product.id}`"><img class="h-auto self-center" :src="product.image" alt="" /></a>
            <h2 class="text-black mt-auto text-sm">{{ product.title }}</h2>
            <p><strong>Price: </strong> {{ product.price }}</p>
        </div>
           </div>
        </main>
    </UContainer>
    <AppFooter />

</div>
</template>