<script setup lang="ts">
import type { FormError, FormErrorEvent, FormSubmitEvent } from "@nuxt/ui";
import { useI18n } from "vue-i18n";

const { t } = useI18n();

const state = reactive({
  name: undefined,
  email: undefined,
  message: undefined,
});

const validate = (state: any): FormError[] => {
  const errors = [];
  if (!state.name)
    errors.push({ name: "name", message: t("contact.form.required") });
  if (!state.email)
    errors.push({ name: "email", message: t("contact.form.required") });
  if (!state.message)
    errors.push({ name: "message", message: t("contact.form.required") });
  return errors;
};

const toast = useToast();
async function onSubmit(event: FormSubmitEvent<any>) {
  toast.add({
    title: t("contact.form.success"),
    description: t("contact.form.success_message"),
    color: "success",
  });
  console.log(event.data);
}

async function onError(event: FormErrorEvent) {
  if (event?.errors?.[0]?.id) {
    const element = document.getElementById(event.errors[0].id);
    element?.focus();
    element?.scrollIntoView({ behavior: "smooth", block: "center" });
  }
}

const features = ref([
  {
    title: t("contact.features.email.title"),
    description: t("contact.features.email.description"),
    icon: "i-lucide-mail",
    to: "mailto:info@theanthropreneur.nl",
  },
  {
    title: t("contact.features.phone.title"),
    description: t("contact.features.phone.description"),
    icon: "i-lucide-phone",
    to: "tel:+31655678901",
  },
  {
    title: t("contact.features.linkedin.title"),
    description: t("contact.features.linkedin.description"),
    icon: "i-lucide-linkedin",
    to: "https://www.linkedin.com/in/vera-de-groot-1a1bb9244",
  },
]);

const isLoading = ref(false);

const handleSubmit = async () => {
  isLoading.value = true;
  // TODO: Implement form submission logic
  isLoading.value = false;
};
</script>

<template>
  <UPageSection
    :title="t('contact.title')"
    :description="t('contact.description')"
    icon="i-lucide-message-circle"
    orientation="horizontal"
    :features="features"
  >
    <UForm
      :validate="validate"
      :state="state"
      @submit="onSubmit"
      @error="onError"
    >
      <div class="flex flex-col space-y-4">
        <div class="flex">
          <UFormField
            :label="t('contact.form.name')"
            name="name"
            class="flex-1"
          >
            <UInput v-model="state.name" />
          </UFormField>

          <UFormField
            :label="t('contact.form.email')"
            name="email"
            class="flex-1"
          >
            <UInput v-model="state.email" class="w-full" />
          </UFormField>
        </div>

        <UFormField
          :label="t('contact.form.message')"
          name="message"
          class="w-full"
        >
          <UTextarea
            size="xl"
            color="neutral"
            v-model="state.message"
            class="w-full"
            rows="5"
          />
        </UFormField>
      </div>

      <UButton style="margin-top: 1rem" type="submit">{{
        t("contact.form.submit")
      }}</UButton>
    </UForm>
  </UPageSection>
</template>
