<template>
    <button
        class="flex h-14 items-center justify-center rounded-[0.25rem] bg-tone-2"
        @click="$emit('click', $event)"
        :class="[
            keyboardKey === 'delete' || keyboardKey === 'enter'
                ? 'w-16'
                : 'w-11',
        ]"
    >
        <svg
            v-if="keyboardKey === 'delete'"
            xmlns="http://www.w3.org/2000/svg"
            height="24"
            viewBox="0 0 24 24"
            width="24"
        >
            <path
                fill="white"
                d="M22 3H7c-.69 0-1.23.35-1.59.88L0 12l5.41 8.11c.36.53.9.89 1.59.89h15c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm0 16H7.07L2.4 12l4.66-7H22v14zm-11.59-2L14 13.41 17.59 17 19 15.59 15.41 12 19 8.41 17.59 7 14 10.59 10.41 7 9 8.41 12.59 12 9 15.59z"
            ></path>
        </svg>
        <span v-else class="font-bold text-white">
            {{ keyboardKey.toUpperCase() }}
        </span>
    </button>
</template>

<script lang="ts" setup>
export type KeyboardKey =
    | 'a'
    | 'b'
    | 'c'
    | 'd'
    | 'e'
    | 'f'
    | 'g'
    | 'h'
    | 'i'
    | 'j'
    | 'k'
    | 'l'
    | 'm'
    | 'n'
    | 'o'
    | 'p'
    | 'q'
    | 'r'
    | 's'
    | 't'
    | 'u'
    | 'v'
    | 'w'
    | 'x'
    | 'y'
    | 'z'
    | 'enter'
    | 'delete'

export interface KeyInputProps {
    keyboardKey: KeyboardKey
}

defineProps<KeyInputProps>()

defineEmits(['click'])
</script>

<style lang="css" scoped></style>
