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
    </ULandingHero>

    <!-- Projects section -->
    <UContainer>
      <h2
        class="text-3xl font-bold tracking-tight text-gray-900 dark:text-white sm:text-4xl lg:text-5xl mb-16 text-center"
      >
        Projects where I work
      </h2>
    </UContainer>

    <div class="flex flex-col gap-32">
      <!-- Project 1 -->

      <UContainer class="grid grid-cols-2 gap-10 justify-center text-left items-center space-x-4">
        <div class="flex flex-col gap-4">
          <h2 class="text-3xl font-bold">COFF</h2>
          <p class="text-xl">
            COFF is an application that utilizes NFTs for the purchasing process of coffe. It lets
            users buy and sell tokens, COFF, which canbe acquired anytime, anywhere, and change them
            at registered stores using the app.
          </p>
          <div class="flex gap-5">
            <UButton
              color="black"
              to="https://coff.ar/"
              label="Live preview"
              size="sm"
              class="rounded-full"
            />
            <UButton
              color="gray"
              to="https://volta.net/changelog"
              label="Github"
              trailing-icon="i-simple-icons-github"
              size="sm"
              class="rounded-full"
            />
          </div>
        </div>

        <div>
          <ULink to="https://coff.ar/">
            <img class="rounded-lg" src="/public/img/coff.png" alt="" />
          </ULink>
        </div>
      </UContainer>

      <!-- Project 2 -->

      <UContainer class="grid grid-cols-2 gap-10 justify-center text-left items-center space-x-4">
        <ULink to="https://vegy.ar/">
          <img class="rounded-lg" src="/public/img/vegy.png" alt="" />
        </ULink>
        <div class="flex flex-col gap-4">
          <h2 class="text-3xl font-bold">Vegy</h2>
          <p class="text-xl">
            COFF is an application that utilizes NFTs for the purchasing process of coffe. It lets
            users buy and sell tokens, COFF, which can be acquired anytime, anywhere, and change
            them at registered stores using the app.
          </p>
          <div class="flex gap-5">
            <UButton
              color="black"
              to="https://vegy.ar/"
              label="Live preview"
              size="sm"
              class="rounded-full"
            />
            <UButton
              color="gray"
              to="https://volta.net/changelog"
              label="Github"
              trailing-icon="i-simple-icons-github"
              size="sm"
              class="rounded-full"
            />
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
          <div class="flex gap-5">
            <UButton
              color="black"
              to="https://codecave.ar/"
              label="Live preview"
              size="sm"
              class="rounded-full"
            />
            <UButton
              color="gray"
              to="https://volta.net/changelog"
              label="Github"
              trailing-icon="i-simple-icons-github"
              size="sm"
              class="rounded-full"
            />
          </div>
        </div>
        <ULink to="https://codecave.ar/">
          <img class="rounded-lg" src="/public/img/codeCave.png" alt="" />
        </ULink>
      </UContainer>
    </div>

    <ULandingSection :title="page.features.title" :description="page.features.description">
      <UPageGrid>
        <ULandingCard v-for="(item, index) in page.features.items" :key="index" v-bind="item" />
      </UPageGrid>
    </ULandingSection>
    <UContainer class="py-32">
      <h2
        class="text-3xl font-bold tracking-tight text-gray-900 dark:text-white sm:text-4xl lg:text-5xl mb-16 text-center"
      >
        You want to contact me?
      </h2>
      <ULandingLogos>
        <a href="https://github.com/LighuenR"
          ><UIcon name="i-simple-icons-github" class="w-10 h-10 flex-shrink-0"
        /></a>
        <a href="https://www.discordapp.com/users/698376865718730812"
          ><UIcon name="i-simple-icons-discord" class="w-10 h-10 flex-shrink-0"
        /></a>
        <a href="https://twitter.com/LRestanio">
          <UIcon name="i-simple-icons-x" class="w-10 h-10 flex-shrink-0" />
        </a>
        <a href="https://www.linkedin.com/in/lighuen-restanio-436a16211/">
          <UIcon name="i-simple-icons-linkedin" class="w-10 h-10 flex-shrink-0"
        /></a>
      </ULandingLogos>
    </UContainer>
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
