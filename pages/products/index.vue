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
           
        </main>
    </UContainer>
    <AppFooter />

</div>
</template>

<style>


</style>