
<template>
  <button :class="twMerge(button({ intent, size, btnType }))">
    <slot />
  </button>
</template>

<script setup>
import { defineProps } from 'vue'
import { twMerge } from 'tailwind-merge'
import { cva } from "class-variance-authority";

const button = cva([
  'leading-none',
  'flex',
  'gap-2',
  'items-center',
  'justify-center',
  'focus:outline-none',
  'focus-visible:ring-4',
  'transition-all',
  'rounded-lg',
  'ring-red-300',
  'disabled:cursor-not-allowed',
  'px-1.5',
  'py-1.5'
], {
  variants: {
    intent: {
      primary: [
        'bg-red-600',
        'text-red-50',
        'hover:bg-red-500',
        'active:bg-red-700',
        'focus-visible:bg-red-600',
        'disabled:bg-red-50',
        'disabled:bg-red-200',
        'disabled:text-red-400'
      ],
      secondary: [
        'bg-green-600',
        'text-green-50',
        'hover:bg-green-500',
        'active:bg-green-700',
        'focus-visible:bg-green-600',
        'disabled:bg-green-50',
        'disabled:bg-green-200',
        'disabled:text-green-400'
      ],
      tertiary: [
        'bg-yellow-600',
        'text-yellow-50',
        'hover:bg-yellow-500',
        'active:bg-yellow-700',
        'focus-visible:bg-yellow-600',
        'disabled:bg-yellow-50',
        'disabled:bg-yellow-200',
        'disabled:text-yellow-400'
      ]
    },
    size: {
      sm: [
        'text-sm',
        'py-1.5',
        'min-h-9',
        'px-3'
      ],
      md: [
        'text-sm',
        'py-2',
        'min-h-10',
        'px-5'
      ],
      lg: [
        'text-md',
        'py-2.5',
        'min-h-11',
        'px-5'
      ],
      xl: [
        'text-md',
        'py-3',
        'min-h-12',
        'px-6'
      ]
    },
    btnType: {
      button: "",
      icon: [
        'rounded-full'
      ]
    }
  },
  compoundVariants: [
  //   { btnType: "icon", size: "sm", class: "h-10 w-10" },
  //   { btnType: "icon", size: "md", class: "h-11 w-11" },
  //   { btnType: "icon", size: "lg", class: "h-12 w-12" },
    { btnType: "icon", size: "xl", class: "h-30 w-30" },
  ],
  // defaultVarients: {
  //   intent: "primary",
  //   size: "md",
  //   btnType: 'button'
  // }
});



defineProps({
  intent: {
    type: String,
    default: 'primary'
  },
  size: {
    type: String,
    default: 'md'
  },
  btnType: {
    type: String,
    default: 'button'
  }
})

</script>