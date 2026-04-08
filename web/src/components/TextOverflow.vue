<script setup lang="ts">
import { ref } from 'vue'
import BaihuDialog from '@/components/ui/BaihuDialog.vue'

const props = withDefaults(
  defineProps<{
    text: string
    title?: string
  }>(),
  {
    title: '详情'
  }
)

const showDialog = ref(false)

function handleClick() {
  if (props.text && props.text !== '-') {
    showDialog.value = true
  }
}
</script>

<template>
  <span v-bind="$attrs" class="truncate block cursor-pointer hover:text-primary transition-colors" :title="text || '-'"
    @click.stop="handleClick">
    {{ text || '-' }}
  </span>

  <BaihuDialog v-model:open="showDialog" :title="title">
    <div class="max-h-[60vh] overflow-y-auto custom-scrollbar">
      <p class="text-[15px] leading-relaxed text-foreground/80 break-all whitespace-pre-wrap font-sans">
        {{ text }}
      </p>
    </div>
  </BaihuDialog>
</template>
