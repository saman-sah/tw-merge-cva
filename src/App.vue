<template>
  <div>
    <div>
    <ButtonCustom>
      <span>Button</span>
      <span>&rarr;</span>
    </ButtonCustom>
    <ButtonCustom btnType="icon" intent="secondary" size="xl">
      <span>&rarr;</span>
    </ButtonCustom>
  </div>
  <div>
    <table class="variant-table">
    <thead>
      <tr>
        <th></th>
        <th v-for="intent in intents" :key="intent">
          {{ intent || "default" }}
        </th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="size in sizes" :key="size">
        <th scope="row">{{ size || "default" }}</th>

        <td v-for="(intent, index) in intents" :key="index">
          <ButtonCva :intent="intent" :size="size"
            >{{ intent || "default" }} 
            <span>Button</span>
            <span>&rarr;</span>
          </ButtonCva>
          <ButtonCva :intent="intent" :size="size" btnType="icon"
            >
            <span>&rarr;</span>
          </ButtonCva>
        </td>
      </tr>
    </tbody>
  </table>
  </div>
  </div>
</template>

<script setup lang="ts">
import ButtonCva from "@/components/ButtonCva.vue";
import ButtonCustom from "@/components/ButtonCustom.vue";

const intents = [undefined, "primary", "secondary", "tertiary"] as const;
const sizes = [undefined, "sm", "md", "lg", "xl"] as const;
</script>
<style scoped>
.variant-table {
  position: relative;
  height: max-content;
  width: max-content;
  align-self: center;
  justify-self: center;
}

.variant-table :where(th, td) {
  padding: 0.5rem;
}
</style>