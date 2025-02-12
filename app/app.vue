<script setup>
import { en, nl } from "@nuxt/ui/locale";

// Add browser language detection with SSR support
const { locale, setLocale } = useI18n({
  legacy: false,
  fallbackLocale: "nl",
  initialLocale: computed(() => {
    if (process.server) {
      const headers = useRequestHeaders();
      const acceptLanguage = headers["accept-language"]?.split(",")[0] || "nl";
      return acceptLanguage.startsWith("en") ? "en" : "nl";
    }
    return navigator?.language?.startsWith("en") ? "en" : "nl";
  }),
});

// Watch for locale changes and update i18n
watch(locale, (newLocale) => {
  setLocale(newLocale);
});

const route = useRoute();

const items = computed(() => [
  {
    label: "Over mij",
    to: "/over-mij",
  },
  // {
  //   label: "Mijn werk",
  //   to: "/mijn-werk",
  // },
  // {
  //   label: "Diensten",
  //   to: "/diensten",
  // },
  //   {
  //   label: "Blog",
  //   to: "/blog",
  // },
  {
    label: "Contact",
    to: "/contact",
  },
]);

useHead({
  meta: [{ name: "viewport", content: "width=device-width, initial-scale=1" }],
  link: [{ rel: "icon", href: "/favicon.ico" }],
  htmlAttrs: {
    lang: "en",
  },
});

const title = "Nuxt UI Pro - Starter";
const description =
  "Nuxt UI Pro is a collection of premium Vue components built on top of Nuxt UI to create beautiful & responsive Nuxt applications in minutes.";

useSeoMeta({
  title,
  description,
  ogTitle: title,
  ogDescription: description,
  ogImage: "https://ui-pro-starter.nuxt.dev/social-card.png",
  twitterImage: "https://ui-pro-starter.nuxt.dev/social-card.png",
  twitterCard: "summary_large_image",
});
</script>

<template>
  <UApp :locale="{ en, nl }[locale]">
    <UHeader>
      <template #title> The Anthropologist </template>

      <UNavigationMenu :items="items" />

      <template #right>
        <ULocaleSelect v-model="locale" :locales="[en, nl]" />
        <UColorModeButton />
      </template>

      <template #content>
        <UNavigationMenu
          :items="items"
          orientation="vertical"
          class="-mx-2.5"
        />
      </template>
    </UHeader>

    <UMain>
      <NuxtPage />
    </UMain>

    <USeparator icon="i-lucide-handshake" />

    <UFooter>
      <template #left>
        <p class="text-(--ui-text-muted)">
          Copyright © {{ new Date().getFullYear() }} The Anthropreneur
        </p>
      </template>

      <template #right>
        <UButton
          icon="i-simple-icons-instagram"
          color="neutral"
          variant="ghost"
          to="https://www.instagram.com/theanthropreneur"
          target="_blank"
          aria-label="Instagram"
        />
        <UButton
          icon="i-simple-icons-linkedin"
          color="neutral"
          variant="ghost"
          to="https://www.linkedin.com/in/vera-de-groot-1a1bb9244"
          target="_blank"
          aria-label="LinkedIn"
        />
        <UButton
          icon="i-simple-icons-x"
          color="neutral"
          variant="ghost"
          to="https://x.com/theanthropreneur"
          target="_blank"
          aria-label="X"
        />
      </template>
    </UFooter>
  </UApp>
</template>
