<template>
  <div class="container">
    <h1>Social Share Buttons</h1>

    <h2>styled = true, label = true</h2>

    <div class="buttons">
      <SocialShare
        v-for="network in testNetworks"
        :key="network"
        :network="network"
        :styled="true"
        :label="true"
      />
    </div>

    <h2>styled = true, label = false</h2>

    <div class="buttons">
      <SocialShare
        v-for="network in testNetworks"
        :key="network"
        :network="network"
        :styled="true"
        :label="false"
      />
    </div>

    <h2>styled = true, label = false, with custom style</h2>

    <div class="buttons buttons-square">
      <SocialShare
        v-for="network in testNetworks"
        :key="network"
        :network="network"
        :styled="true"
        :label="false"
        class="button-square"
      />
    </div>

    <h2>defaults (styled = false, label = true)</h2>

    <div class="buttons">
      <SocialShare
        v-for="network in testNetworks"
        :key="network"
        :network="network"
      />
    </div>

    <h2>composable output</h2>
    <pre>{{ testComposable }}</pre>
  </div>
</template>

<script setup>
import { networksIndex } from '../src/runtime/networksIndex'
import { useSocialShare } from '#imports'

const testComposable = useSocialShare({ network: 'facebook' })

const testNetworks = Object.keys(networksIndex)
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
.buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  border: 2px solid lightgray;
  padding: 2rem;
  width: max-content;
}
.buttons-square {
  gap: 0rem;
}
.button-square {
  padding: 1rem;
  font-size: 1rem;
  border-radius: 0;
}

pre {
  background-color: lightgray;
  padding: 1rem;
  font-family: monospace;
  max-width: max-content;
}
</style>
