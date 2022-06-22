<template>
    <div class="flex min-h-screen flex-col bg-tone-7">
        <header
            class="flex h-14 items-center space-x-4 border-b border-b-tone-4 px-4"
        >
            <span
                class="flex-1 text-center text-4xl font-bold leading-none tracking-[0.01em] text-white"
            >
                Wordle
            </span>
        </header>
        <main class="container mx-auto flex flex-1 flex-col px-4">
            <div class="flex flex-1 items-center justify-center">
                <div class="grid max-w-[340px] grid-cols-5 grid-rows-6 gap-1">
                    <template v-for="i in rows">
                        <template v-for="j in columns" :key="`${i}-${j}`">
                            <LetterBox
                                v-model="typedLetters[j - 1]"
                                :value="correctWord[j - 1]"
                                :disabled="
                                    i - 1 !== currentRow ||
                                    j - 1 > currentColumn
                                "
                                ref="letterBoxRefs"
                                @letter-input="onLetterInput(i - 1, j - i)"
                            />
                        </template>
                    </template>
                </div>
            </div>
            <GameKeyboard></GameKeyboard>
        </main>
    </div>
</template>

<script lang="ts" setup>
import GameKeyboard from '@/components/GameKeyboard.vue'
import LetterBox from '@/components/LetterBox.vue'
import { useMagicKeys, whenever } from '@vueuse/core'
import { onMounted, ref } from 'vue'

const columns = ref(5)
const rows = ref(6)

const keys = useMagicKeys()

const typedLetters = ref<string[]>([])
const correctWord = ref('Nique'.toUpperCase())
const currentRow = ref(0)
const currentColumn = ref(0)

const letterBoxRefs = ref<InstanceType<typeof LetterBox>[] | null[]>([])

const onLetterInput = (row: number, column: number) => {
    if (currentColumn.value < 5) currentColumn.value++
    console.log('row', row)
    console.log('column', column)
    console.log(letterBoxRefs.value[row * column]?.inputRef)
    // letterBoxRefs.value[row * column]?.inputRef?.focus()
}

// onStartTyping(() => {
//     console.log(letterBoxRefs.value[]?.inputRef?.focus())
// })

whenever(keys.Enter, () => {
    console.log('Enter pressed')
})

onMounted(() => {
    console.log(letterBoxRefs.value)
})
</script>

<style lang="css" scoped></style>
