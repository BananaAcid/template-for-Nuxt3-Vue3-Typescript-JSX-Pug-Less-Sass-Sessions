<template lang="pug">
nav
    li: NuxtLink(to="/") Home
    //- "two" => automatically resolves to "/pages/two.vue"
    li: NuxtLink(to="/two") Two
</template>
