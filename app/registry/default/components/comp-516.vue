<script setup lang="ts">
import { Button } from "@/registry/default/ui/button";
import {
  Stepper,
  StepperIndicator,
  StepperItem,
  StepperSeparator,
  StepperTrigger,
} from "@/registry/default/ui/stepper";
import { ref } from "vue";

const steps = [1, 2, 3, 4];
const currentStep = ref(2);
</script>

<template>
  <div class="mx-auto max-w-xl space-y-8 text-center">
    <Stepper v-model="currentStep">
      <StepperItem
        v-for="step in steps"
        :key="step"
        :step="step"
        :class="step !== steps.length ? 'flex-1' : ''"
      >
        <StepperTrigger as-child>
          <StepperIndicator />
        </StepperTrigger>
        <StepperSeparator v-if="step < steps.length" />
      </StepperItem>
    </Stepper>
    <div class="flex justify-center space-x-4">
      <Button
        variant="outline"
        class="w-32"
        @click="currentStep = currentStep - 1"
        :disabled="currentStep === 1"
      >
        Prev step
      </Button>
      <Button
        variant="outline"
        class="w-32"
        @click="currentStep = currentStep + 1"
        :disabled="currentStep > steps.length"
      >
        Next step
      </Button>
    </div>
    <p
      class="text-muted-foreground mt-2 text-xs"
      role="region"
      aria-live="polite"
    >
      Controlled stepper with checkmarks
    </p>
  </div>
</template>
