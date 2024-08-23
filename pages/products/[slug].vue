<script setup lang="ts">
const route = useRoute();
console.log(route.params.id);
/* only pick the fields used in your template */
const { status, data: product } = await useFetch('https://fakestoreapi.com/products/' + route.params.slug,
    {
        pick: ['title',
            'description',
            'image',
            'price']
    })
</script>
<template>
    <div>
        <AppHeader />
        <UContainer>
            <main class="conatiner mx-auto p-4 product-detail">
                <ContentDoc>
                    <template v-slot="{ doc }">
                        <article>
                            <h1 class="text-2xl product-name">{{ doc.title }}</h1>
                            <ContentRenderer :value="doc" />
                        </article>
                    </template>
                    <template #not-found>
                        <!-- <h1>Page not found</h1> -->
                    </template>
                </ContentDoc>
                <div v-if="product.image" class="addtional-product">
                    <img class="h-auto self-center" :src="product.image" alt="" />
                    <h1 class="text-2xl product-name">{{ product.title }}</h1>
                    <p><strong>Price: </strong> {{ product.price }}</p>
                    <p>{{ product.description }}</p>

                </div>
            </main>
        </UContainer>
        <AppFooter />

    </div>
</template>
