<script setup lang="ts">
import { useI18n } from "vue-i18n";

const { t } = useI18n();

const sections = [
  {
    text: "",
  },
  {
    text: `Mijn aanpak is geworteld in een antropologische 'bottom-up' methode, waarbij ik de behoeften en dynamiek van een community in kaart breng voordat er strategische beslissingen worden genomen. Dit zorgt ervoor dat de oplossingen die ik bied – of het nu gaat om community building, bedrijfscultuur of interpersoonlijke verbindingen – niet alleen effectief, maar ook authentiek en toekomstbestendig zijn. Dit doe ik door middel van consultancy en workshops, maar ook freelance projecten waarin ik organisaties begeleid bij het maken van bewuste keuzes rondom verbinding en samenwerking.`,
  },
  {
    text: "Verbinding staat bij mij centraal: luisteren, inclusiviteit en intentionaliteit vormen de kern van mijn werk. Ik geloof dat sterke communities de basis zijn voor succesvolle organisaties en dat impact ontstaat door echte interactie. Als The Anthropreneur wil ik een brug slaan tussen mens en organisatie, omdat ik geloof dat organisaties meer succes boeken wanneer zij investeren in de mensen die er onderdeel van uitmaken. Door te focussen op verbinding, betrokkenheid en een sterke community, help ik hen een omgeving te creëren waarin zowel individuen als de organisatie kunnen floreren.",
  },
];
</script>

<template>
  <UPage>
    <UPageSection
      :title="t('about.intro.title')"
      :description="t('about.intro.description')"
      orientation="horizontal"
      reverse
    >
      <img
        src="/vera.jpg"
        width="704"
        height="647"
        alt="Illustration"
        class="w-full rounded-[calc(var(--ui-radius)*2)]"
      />
    </UPageSection>
    <UPageSection
      orientation="horizontal"
      :title="t('about.approach.title')"
      :description="t('about.approach.description')"
    >
      <img
        src="https://picsum.photos/704"
        width="704"
        height="647"
        alt="Illustration"
        class="rounded-[calc(var(--ui-radius)*2)]"
      />
    </UPageSection>
    <UPageSection
      :title="t('about.vision.title')"
      orientation="horizontal"
      reverse
      :description="t('about.vision.description')"
    >
      <img
        src="https://picsum.photos/704"
        alt="Illustration"
        class="rounded-[calc(var(--ui-radius)*2)]"
      />
    </UPageSection>
  </UPage>
</template>

<style scoped>
.prose p {
  margin-bottom: 1.5em;
}
</style>
