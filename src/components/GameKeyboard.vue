<template>
    <div class="mb-2 flex flex-col space-y-1.5">
        <div class="flex justify-center space-x-1.5">
            <template
                v-for="keyboardKey in firstKeyboardRow"
                :key="keyboardKey"
            >
                <KeyInput :keyboard-key="keyboardKey"></KeyInput>
            </template>
        </div>
        <div class="flex justify-center space-x-1.5">
            <template
                v-for="keyboardKey in secondKeyboardRow"
                :key="keyboardKey"
            >
                <KeyInput :keyboard-key="keyboardKey"></KeyInput>
            </template>
        </div>
        <div class="flex justify-center space-x-1.5">
            <template
                v-for="keyboardKey in thirdKeyboardRow"
                :key="keyboardKey"
            >
                <KeyInput :keyboard-key="keyboardKey"></KeyInput>
            </template>
        </div>
    </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import type { KeyboardKey } from './KeyInput.vue'
import KeyInput from './KeyInput.vue'

const firstKeyboardRow = ref<KeyboardKey[]>([
    'q',
    'w',
    'e',
    'r',
    't',
    'y',
    'u',
    'i',
    'o',
    'p',
])

const secondKeyboardRow = ref<KeyboardKey[]>([
    'a',
    's',
    'd',
    'f',
    'g',
    'h',
    'j',
    'k',
    'l',
])

const thirdKeyboardRow = ref<KeyboardKey[]>([
    'enter',
    'z',
    'x',
    'c',
    'v',
    'b',
    'n',
    'm',
    'delete',
])
</script>

<style lang="css" scoped></style>
