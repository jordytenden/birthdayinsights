<template>
    <Html :lang="head.htmlAttrs.lang" :dir="head.htmlAttrs.dir">
    <Head>
        <Title>{{ title }}</Title>
        <template v-for="link in head.link" :key="link.id">
            <Link :id="link.id" :rel="link.rel" :href="link.href" :hreflang="link.hreflang" />
        </template>
        <template v-for="meta in head.meta" :key="meta.id">
            <Meta :id="meta.id" :property="meta.property" :content="meta.content" />
        </template>
    </Head>
    <Body>
        <main>
            <NuxtPage />
        </main>
    </Body>
    </Html>
</template>

<script lang="ts" setup>
    import { useRoute, useI18n, useLocaleHead } from '#imports';

    const head = useLocaleHead({
        addDirAttribute    : true,
        identifierAttribute: 'id',
        addSeoAttributes   : true
    });
</script>
