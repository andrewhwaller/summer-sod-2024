<script setup lang="ts">
  import { computed } from 'vue'
  import { handleBackground } from '../layoutHelper'
  import { resolveAssetUrl } from '../layoutHelper'

  const props = defineProps({
    image: {
      type: String,
    },
    class: {
      type: String,
    },
    backgroundSize: {
      type: String,
      default: 'contain'
    },
    work: {
      type: String,
    },
    metadata: {
      type: String,
    },
  })

  const style = {
    backgroundImage : `url(${resolveAssetUrl(props.image)})`,
    backgroundSize: props.backgroundSize,
    backgroundPosition: 'right',
    backgroundRepeat: 'no-repeat',
  }
</script>

<template>
  <div class="grid grid-cols-2 w-full h-full auto-rows-fr">
    <div class="slidev-layout default flex flex-col pl-2 pb-2" :class="props.class">
      <div class="px-4">
        <slot/>
      </div>
      <div class="mt-auto flex flex-col">
        <span class="text-1xl font-italic leading-tight dark:text-white">{{ props.work }}</span>
        <span class="text-1xl leading-tight dark:text-white">{{ props.metadata }}</span>
      </div>
    </div>
    <div class="w-full h-full" :style="style" />
  </div>
</template>
