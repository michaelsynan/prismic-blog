<script setup lang="ts">
const route = useRoute()

</script>

<template>
  <div class="text-slate-700">
    <!-- TODO: Remove the following element once you have read the documentation. -->
    <DevOnly>
      <div
        :style="{
          background: '#5163ba',
          padding: '1rem',
          textAlign: 'center',
          fontSize: '0.85rem',
          color: '#fff'
        }"
      >
        <p>
      
        </p>
      </div>
    </DevOnly>
    <Header
      :with-profile="route.meta.withHeaderProfile"
      :with-divider="route.meta.withHeaderDivider"
    />
    <slot />
    <Footer :with-sign-up-form="route.meta.withFooterSignUpForm" />
  </div>
</template>
