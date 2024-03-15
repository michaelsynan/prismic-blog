<script setup lang="ts">
defineProps({
  withDivider: {
    type: Boolean,
    default: true,
  },
  withProfile: {
    type: Boolean,
    default: true
  }
})

const navigation = useNavigation()
const settings = useSettings()

const colorMode = useColorMode()

function toggleColorMode() {
  colorMode.value = colorMode.value === 'dark' ? 'light' : 'dark';
}

</script>

<template>
  <Bounded as="header">
    <div class="grid grid-cols-1 justify-items-center gap-20">
      <nav>
        <ul class="flex flex-wrap justify-center gap-10">
          <HeaderNavItem>
            <NuxtLink to="/">
              {{ $prismic.asText(navigation?.data.homepageLabel) }}
            </NuxtLink>
          </HeaderNavItem>
          <HeaderNavItem
            v-for="item in navigation?.data.links"
            :key="$prismic.asText(item.label)"
          >
            <PrismicLink :field="item.link">
              {{ $prismic.asText(item.label) }}
            </PrismicLink>
          </HeaderNavItem>
          <div @click="toggleColorMode" class="cursor-pointer font-bold flex items-center">
            <Icon v-if="colorMode.value === 'dark'" name="uil:sun"  class="text-lg importantIcon" />
            <Icon v-else name="uil:moon" class="text-lg importantIcon" />
          </div>
        </ul>
      </nav>
      <HeaderProfile
        v-if="withProfile"
        :name="settings?.data.name"
        :description="settings?.data.description"
        :profile-picture="settings?.data.profilePicture"
      />
      <HorizontalDivider v-if="withDivider" />
    </div>
  </Bounded>
</template>
