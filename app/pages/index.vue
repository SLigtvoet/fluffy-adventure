<script setup lang="ts">
import { useI18n } from "vue-i18n";

const { t } = useI18n();

const features = ref([
  {
    title: t("services.features.consultancy.title"),
    description: t("services.features.consultancy.description"),
    icon: "i-lucide-users",
  },
  {
    title: t("services.features.workshops.title"),
    description: t("services.features.workshops.description"),
    icon: "i-lucide-globe",
  },
  {
    title: t("services.features.freelance.title"),
    description: t("services.features.freelance.description"),
    icon: "i-lucide-heart",
  },
]);

const testimonials = ref([
  {
    user: {
      name: t("testimonials.items.0.name"),
      description: t("testimonials.items.0.role"),
      avatar: {
        src: "https://avatars.githubusercontent.com/u/499550?v=4",
        alt: t("testimonials.items.0.name"),
      },
    },
    quote: t("testimonials.items.0.quote"),
  },
  {
    user: {
      name: t("testimonials.items.1.name"),
      description: t("testimonials.items.1.role"),
      avatar: {
        src: "https://avatars.githubusercontent.com/u/499550?v=4",
        alt: t("testimonials.items.1.name"),
      },
    },
    quote: t("testimonials.items.1.quote"),
  },
  {
    user: {
      name: t("testimonials.items.2.name"),
      description: t("testimonials.items.2.role"),
      avatar: {
        src: "https://avatars.githubusercontent.com/u/499550?v=4",
        alt: t("testimonials.items.2.name"),
      },
    },
    quote: t("testimonials.items.2.quote"),
  },
]);
</script>

<template>
  <div>
    <UPageHero
      :title="t('hero.title')"
      :description="t('hero.description')"
      :ui="{
        root: 'bg-[url(/nasa.jpg)] bg-center bg-cover bg-no-repeat',
        title: 'text-white text-4xl font-bold',
        description: 'text-white text-lg',
      }"
      :links="[
        {
          label: t('nav.discover'),
          to: '/mijn-werk',
          icon: 'i-lucide-square-play',
          size: 'lg',
        },
        {
          label: t('nav.blog'),
          to: '/blog',
          icon: 'i-lucide-box',
          size: 'lg',
          color: 'neutral',
        },
        {
          label: t('nav.contact'),
          to: '/contact',
          icon: 'i-lucide-message-circle',
          size: 'lg',
        },
      ]"
    />
    <UPageSection
      :title="t('intro.title')"
      :description="t('intro.description')"
    >
    </UPageSection>
    <UPageSection
      :title="t('services.title')"
      :description="t('services.description')"
      :features="features"
    >
    </UPageSection>
    <UPageSection :title="t('testimonials.title')">
      <UPageColumns>
        <UPageCard
          v-for="(testimonial, index) in testimonials"
          :key="index"
          variant="subtle"
          :description="testimonial.quote"
          :ui="{
            description:
              'before:content-[open-quote] after:content-[close-quote]',
          }"
        >
          <template #footer>
            <UUser v-bind="testimonial.user" size="xl" />
          </template>
        </UPageCard>
      </UPageColumns>
    </UPageSection>
    <UPageSection>
      <UPageCTA
        :title="t('cta.title')"
        :description="t('cta.description')"
        variant="subtle"
        :links="[
          {
            label: t('nav.contact'),
            to: '/contact',
            icon: 'i-lucide-message-circle',
            size: 'lg',
            color: 'neutral',
          },
        ]"
      />
    </UPageSection>
  </div>
</template>
