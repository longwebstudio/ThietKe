<script setup lang="ts">
const colorMode = useColorMode()

const color = computed(() => colorMode.value === 'dark' ? '#171717' : 'white')

useHead({
  meta: [
    { name: 'viewport', content: 'width=device-width, initial-scale=1' },
    { key: 'theme-color', name: 'theme-color', content: color }
  ],
  link: [
    { rel: 'icon', href: '/favicon.ico' }
  ],
  htmlAttrs: {
    lang: 'en'
  }
})
const { isLoading } = useLoadingIndicator()
const appear = ref(false)
const appeared = ref(false)

useSeoMeta({
  ogImage: 'https://i0.wp.com/longwebstudio.net/wordpress/wp-content/uploads/2025/07/Toi-giup-doanh-nghiep-nho-co-website-chuyen-nghiep-%E2%80%93-ngay-ca-khi-ban-chua-biet-bat-dau-tu-dau.-1.png',
  twitterImage: 'https://i0.wp.com/longwebstudio.net/wordpress/wp-content/uploads/2025/07/Toi-giup-doanh-nghiep-nho-co-website-chuyen-nghiep-%E2%80%93-ngay-ca-khi-ban-chua-biet-bat-dau-tu-dau.-1.png',
  twitterCard: 'summary_large_image'
})

onMounted(() => {
  setTimeout(() => {
    appear.value = true
    setTimeout(() => {
      appeared.value = true
    }, 1000)
  }, 0)
})
</script>

<template>
  <UApp :toaster="{ expand: false }">
    <!-- <AppHeader /> -->

    <UMain class="relative">
      <HeroBackground
        class="absolute w-full -top-px transition-all text-primary shrink-0"
        :class="[
          isLoading ? 'animate-pulse' : (appear ? '' : 'opacity-0'),
          appeared ? 'duration-[400ms]': 'duration-1000'
        ]"
      />
      <NuxtPage />
    </UMain>

    <!-- <AppFooter /> -->
  </UApp>
</template>
