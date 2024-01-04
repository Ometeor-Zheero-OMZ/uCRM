<script setup>
import { Link } from "@inertiajs/inertia-vue3";
</script>

<template>
    Inertia Test <br />
    <a href="/">a tag</a><br />
    <Link href="/">Link tag</Link><br />
    <Link :href="route('inertia.index')">named route</Link>
</template>
