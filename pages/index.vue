<script setup lang="ts">
const { data: page } = await useAsyncData('index', () => queryContent('/').findOne())
if (!page.value) {
  throw createError({
    statusCode: 404,
    statusMessage: 'Page not found',
    fatal: true
  })
}

useSeoMeta({
  titleTemplate: '',
  title: page.value.title,
  ogTitle: page.value.title,
  description: page.value.description,
  ogDescription: page.value.description
})
</script>

<template>
  <div v-if="page">
    <ULandingHero
      :title="page.hero.title"
      :description="page.hero.description"
      :links="page.hero.links"
    >
      <div
        class="absolute inset-0 landing-grid z-[-1] [mask-image:radial-gradient(100%_100%_at_top_right,white,transparent)]"
      />

      <template #headline>
        <UBadge
          v-if="page.hero.headline"
          variant="subtle"
          size="lg"
          class="relative rounded-full font-semibold"
        >
          <NuxtLink
            :to="page.hero.headline.to"
            target="_blank"
            class="focus:outline-none"
            tabindex="-1"
          >
            <span class="absolute inset-0" aria-hidden="true" />
          </NuxtLink>

          {{ page.hero.headline.label }}

          <UIcon
            v-if="page.hero.headline.icon"
            :name="page.hero.headline.icon"
            class="ml-1 w-4 h-4 pointer-events-none"
          />
        </UBadge>
      </template>
    </ULandingHero>
    <!-- Projects section -->
    <div class="flex flex-col gap-40">
      <UContainer>
        <h2
          class="text-3xl font-bold tracking-tight text-gray-900 dark:text-white sm:text-4xl lg:text-5xl"
        >
          Projects where I work
        </h2>
      </UContainer>

      <!-- Project 1 -->

      <UContainer class="grid grid-cols-2 gap-10 justify-center text-left items-center space-x-4">
        <div class="flex flex-col gap-4">
          <h2 class="text-3xl font-bold">COFF</h2>
          <p class="text-xl">
            COFF is an application that utilizes NFTs for the purchasing process of coffe. It lets
            users buy and sell tokens, COFF, which can be acquired anytime, anywhere, and change
            them at registered stores using the app.
          </p>
          <div class="gap-2 flex">
            <UIcon name="i-simple-icons-github" class="w-7 h-7 flex-shrink-0" />
            <UIcon name="i-simple-icons-discord" class="w-7 h-7 flex-shrink-0" />
            <UIcon name="i-simple-icons-x" class="w-7 h-7 flex-shrink-0" />
            <UIcon name="i-simple-icons-instagram" class="w-7 h-7 flex-shrink-0" />
            <UIcon name="i-simple-icons-linkedin" class="w-7 h-7 flex-shrink-0" />
            <UIcon name="i-simple-icons-facebook" class="w-7 h-7 flex-shrink-0" />
          </div>
        </div>

        <div><img class="rounded-lg" src="/public/img/coff.png" alt="" /></div>
      </UContainer>

      <!-- Project 2 -->

      <UContainer class="grid grid-cols-2 gap-10 justify-center text-left items-center space-x-4">
        <div><img class="rounded-lg" src="/public/img/vegy.png" alt="" /></div>
        <div class="flex flex-col gap-4">
          <h2 class="text-3xl font-bold">Vegy</h2>
          <p class="text-xl">
            COFF is an application that utilizes NFTs for the purchasing process of coffe. It lets
            users buy and sell tokens, COFF, which can be acquired anytime, anywhere, and change
            them at registered stores using the app.
          </p>
          <div class="gap-2 flex">
            <UIcon name="i-simple-icons-github" class="w-7 h-7 flex-shrink-0" />
            <UIcon name="i-simple-icons-discord" class="w-7 h-7 flex-shrink-0" />
            <UIcon name="i-simple-icons-x" class="w-7 h-7 flex-shrink-0" />
            <UIcon name="i-simple-icons-instagram" class="w-7 h-7 flex-shrink-0" />
            <UIcon name="i-simple-icons-linkedin" class="w-7 h-7 flex-shrink-0" />
            <UIcon name="i-simple-icons-facebook" class="w-7 h-7 flex-shrink-0" />
          </div>
        </div>
      </UContainer>

      <!-- Project 3 -->

      <UContainer class="grid grid-cols-2 gap-10 justify-center text-left items-center space-x-4">
        <div class="flex flex-col gap-4">
          <h2 class="text-3xl font-bold">codeCave Webpage</h2>
          <p class="text-xl">
            COFF is an application that utilizes NFTs for the purchasing process of coffe. It lets
            users buy and sell tokens, COFF, which can be acquired anytime, anywhere, and change
            them at registered stores using the app.
          </p>
          <div class="gap-2 flex">
            <UIcon name="i-simple-icons-github" class="w-7 h-7 flex-shrink-0" />
            <UIcon name="i-simple-icons-discord" class="w-7 h-7 flex-shrink-0" />
            <UIcon name="i-simple-icons-x" class="w-7 h-7 flex-shrink-0" />
            <UIcon name="i-simple-icons-instagram" class="w-7 h-7 flex-shrink-0" />
            <UIcon name="i-simple-icons-linkedin" class="w-7 h-7 flex-shrink-0" />
            <UIcon name="i-simple-icons-facebook" class="w-7 h-7 flex-shrink-0" />
          </div>
        </div>

        <div><img class="rounded-lg" src="/public/img/codecave.png" alt="" /></div>
      </UContainer>
    </div>

    <ULandingSection :title="page.features.title" :description="page.features.description">
      <UPageGrid>
        <ULandingCard v-for="(item, index) in page.features.items" :key="index" v-bind="item" />
      </UPageGrid>
    </ULandingSection>
  </div>
</template>

<style scoped>
.landing-grid {
  background-size: 100px 100px;
  background-image: linear-gradient(to right, rgb(var(--color-gray-200)) 1px, transparent 1px),
    linear-gradient(to bottom, rgb(var(--color-gray-200)) 1px, transparent 1px);
}
.dark {
  .landing-grid {
    background-image: linear-gradient(to right, rgb(var(--color-gray-800)) 1px, transparent 1px),
      linear-gradient(to bottom, rgb(var(--color-gray-800)) 1px, transparent 1px);
  }
}
</style>
