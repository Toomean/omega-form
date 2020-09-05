<template>
  <div class="signup-form">
    <h1 class="signup-form__title">
        {{ $t('signup.title') }}
    </h1>

    <ValidationObserver
      class="signup-form__form"
      tag="form"
      v-slot="{ handleSubmit }"
      @submit.prevent
    >
      <div class="signup-form__row">
        <div class="signup-form__col">
          <ValidationProvider
            rules="required"
            mode="eager"
            :name="$t('signup.firstName')"
            v-slot="{ errors }"
          >
            <form-input
              v-model="formData.firstName"
              type="text"
              :placeholder="$t('signup.firstName')"
              :error="errors[0]"
            />
          </ValidationProvider>
        </div>

        <div class="signup-form__col">
          <ValidationProvider
            rules="required"
            mode="eager"
            :name="$t('signup.lastName')"
            v-slot="{ errors }"
          >
            <form-input
              v-model="formData.lastName"
              type="text"
              :placeholder="$t('signup.lastName')"
              :error="errors[0]"
            />
          </ValidationProvider>
        </div>
      </div>

      <div class="signup-form__row">
        <div class="signup-form__col">
          <ValidationProvider
            rules="required"
            mode="eager"
            v-slot="{ errors }"
            :name="$t('signup.phone')"
          >
            <form-input
              v-model="formData.phone"
              type="text"
              :placeholder="$t('signup.phone')"
              :error="errors[0]"
              :mask="{ mask: '(+44) #### ######' }"
            />
          </ValidationProvider>
        </div>
      </div>

      <div class="signup-form__row">
        <div class="signup-form__col">
          <ValidationProvider
            rules="required|email"
            mode="eager"
            v-slot="{ errors }"
            :name="$t('signup.email')"
          >
            <form-input
              v-model="formData.email"
              type="text"
              :placeholder="$t('signup.email')"
              :error="errors[0]"
            />
          </ValidationProvider>
        </div>
      </div>

      <div class="signup-form__footer">
        <button
          type="submit"
          @click="handleSubmit"
        >
          {{ $t('signup.createAccount') }}
        </button>
      </div>
    </ValidationObserver>
  </div>
</template>

<script>
import FormInput from '@/components/ui/FormInput';

export default {
  components: {
    FormInput,
  },
  data() {
    return {
      formData: {
        firstName: '',
        lastName: '',
        phone: '',
        email: '',
      },
    };
  },
};
</script>

<style lang="scss" src="./SignupForm.scss"></style>
