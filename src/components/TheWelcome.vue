<script setup>
import WelcomeItem from "./WelcomeItem.vue";
import DocumentationIcon from "./icons/IconDocumentation.vue";
import ToolingIcon from "./icons/IconTooling.vue";
import EcosystemIcon from "./icons/IconEcosystem.vue";
import CommunityIcon from "./icons/IconCommunity.vue";
import SupportIcon from "./icons/IconSupport.vue";
</script>

<template>
  <WelcomeItem>
    <template #icon>
      <DocumentationIcon />
    </template>
    <template #heading>Our Aim</template>

    Gruntr aims to provide up to date information regarding the availabilty and
    location of public toilets and the facilities they have.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <ToolingIcon />
    </template>
    <template #heading>Features</template>

    Search the map, leave reviews and make sure you always flush the loo.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <EcosystemIcon />
    </template>
    <template #heading>Give A Crap</template>

    Gruntr is partnering with Who Give's a Crap?
    <a
      href="https://au.whogivesacrap.org/pages/about-us"
      target="_blank"
      rel="noopener"
      >Find out more here.</a
    >.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <CommunityIcon />
    </template>
    <template #heading>Community</template>

    Leave feedback and build a safe and inclusive community. Everyone has the
    right to use a toilet that is clean and caters to their needs. Whether you
    have a disability or need parenting facilities, our aim is to help you find
    what you need.
  </WelcomeItem>

  <WelcomeItem>
    <template #icon>
      <SupportIcon />
    </template>
    <template #heading>Australian Public Toilets</template>

    If our website is not working please use the
    <a href="https://toiletmap.gov.au/" target="_blank" rel="noopener"
      >National Public Toilet Map</a
    >.
  </WelcomeItem>
</template>
