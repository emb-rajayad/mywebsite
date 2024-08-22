<template>
    <div class="bg-neutral-300">
        <header class="mx-auto px-4 sm:px-6 lg:px-8 max-w-7xl">
            <nav class="container mx-auto p-4 flex justiy-between">
                <NuxtLink to="/" class="p-4 font-bold">
                    <UKbd size="xl">My Personal Website </UKbd>
                </NuxtLink>
                <ul class="p-4 mx-auto flex gap-4">
                    <li>
                        <NuxtLink to="/"> Home </NuxtLink>
                    </li>
                    <li>
                        <NuxtLink to="/products">Products</NuxtLink>
                    </li>
                    <li>
                        <NuxtLink to="/about-us">About us </NuxtLink>
                    </li>
                    <li>
                        <NuxtLink to="/contact">Contact</NuxtLink>
                    </li>
                </ul>
                <IconsPixelarticonsCart />
            </nav>
        </header>
    </div>
</template>
<script>

export default {
    name: 'AppHeader'
}
</script>