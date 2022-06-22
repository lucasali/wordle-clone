<template>
    <div class="h-16 w-16" :class="[boxAppearance]">
        <input
            ref="inputRef"
            v-model="value"
            type="text"
            :disabled="disabled"
            class="h-full w-full cursor-default bg-transparent text-center text-2xl font-bold uppercase text-white caret-transparent outline-none"
            maxlength="1"
            onkeypress="return /[a-z]/i.test(event.key)"
        />
    </div>
</template>

<script lang="ts" setup>
import { computed, ref } from '@vue/reactivity'

export type BoxStatus = 'present' | 'correct' | 'absent' | 'empty'

export interface LetterBoxProps {
    disabled?: boolean
    status?: BoxStatus
    modelValue?: string
    value: string
}

const props = withDefaults(defineProps<LetterBoxProps>(), {
    status: 'empty',
})

const emit = defineEmits(['update:modelValue', 'letterInput'])

const inputRef = ref<HTMLInputElement | null>(null)

const boxAppearance = computed<string>(() => {
    if (props.modelValue === null) {
        return 'border-2 border-tone-4'
    } else {
        return 'bg-tone-7 text-tone-1 border-2 border-tone-3'
    }

    // if (props.status === 'empty') {
    //     return 'bg-transparent'
    // } else if (props.status === 'correct') {
    //     return 'bg-green'
    // } else if (props.status === 'present') {
    //     return 'bg-dark-yellow'
    // } else {
    //     return 'bg-tone-4'
    // }
})

const value = computed({
    get() {
        return props.modelValue
    },
    set(value) {
        emit('update:modelValue', value)
        emit('letterInput')
    },
})

defineExpose({
    inputRef,
    value,
})
</script>

<style scoped></style>
