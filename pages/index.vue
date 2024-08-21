<script setup lang="ts">
const items = [
  '/images/pexels-pixabay-163046.jpg',
  '/images/pexels-jopwell-2422293.jpg',
  '/images/pexels-danny-meneses-340146-943096.jpg',
  '/images/pexels-morningtrain-18105.jpg'
]
const carouselRef = ref()

onMounted(() => {
  setInterval(() => {
    if (!carouselRef.value) return

    if (carouselRef.value.page === carouselRef.value.pages) {
      return carouselRef.value.select(0)
    }

    carouselRef.value.next()
  }, 3000)
})


</script>
<template>
    <div>
    <AppHeader />
    <UContainer>
        <main class="conatiner mx-auto p-4">
            <UCarousel
            ref="carouselRef"
            v-slot="{ item }"
            :items="items"
            :ui="{ item: 'basis-full' }"
            class="rounded-lg overflow-hidden"
            indicators
            >
              <img :src="item" class="w-full" draggable="false">
            </UCarousel>
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
        </main>
    </UContainer>
    <AppFooter />

</div>
</template>