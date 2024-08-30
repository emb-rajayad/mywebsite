<template>
    <div class="bg-neutral-300 footer">
        <div class="mx-auto px-4 sm:px-6 lg:px-8 max-w-7xl">
            <ul class="p-4 mx-auto flex gap-4">
            <li><NuxtLink to="/"> Home </NuxtLink></li>
            <li><NuxtLink to="/products">Products</NuxtLink></li>
            <li><NuxtLink to="/about-us">About us </NuxtLink></li>
            <li><NuxtLink to="/contact">Contact</NuxtLink></li>
           </ul>
        <div class="gap-4 copyright">Copyright © 2024-present my personal website, Inc. All rights reserved.</div>
    </div>
    </div>
</template>
<script>
export default {
    name: 'AppFooter'
}
</script>