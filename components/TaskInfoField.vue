<template>
    <div class="flex">
        <span class="font-bold text-black dark:text-white">{{ name }}</span>
        <span class="mr-1">: </span>
        <slot
            ><span :class="valueClass">{{ value }}</span></slot
        >
    </div>
</template>
<script>
import { DurationWithStyle } from "~/types/common/durationWithStyle";

export default {
    props: {
        name: {
            type: String,
            required: true,
        },
        value: {
            type: [Number, String, BigInt, DurationWithStyle],
            default: null,
        },
    },
    computed: {
        valueClass() {
            return this.value instanceof DurationWithStyle
                ? this.value.class
                : "";
        },
    },
};
</script>
