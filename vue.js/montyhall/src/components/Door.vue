<template>
    <div class="door-area">
        <div class="door-frame" :class="{ selected: selected && !open }">
            <Gift v-if="open && hasGift" />
        </div>
        <div class="door" :class="{ open }"
            @click="selected = !selected">
            <div class="number" :class="{ selected }">{{ number }}</div>
            <div class="knob" :class="{ selected }"
                @click.stop="open = true"></div>
        </div>
    </div>
</template>

<script>
import Gift from './Gift'
export default {
    name: 'Door',
    components: { Gift },
    props: {
        number: {},
        hasGift: { type: Boolean }
    },
    data: function() {
        return {
            open: false,
            selected: false
        }
    }
}
</script>

<style>
:root {
    --door-border: 5px solid rgb(128, 58, 9);
    --selected-border: 5px solid yellow;
}
.door-area {
    position: relative;
    width: 200px;
    height: 310px;
    border-bottom: 10px solid rgb(122, 122, 122);
    margin-bottom: 20px;
    font-size: 3rem;
    display: flex;
    justify-content: center;
}
.door-frame {
    position: absolute;
    height: 300px;
    width: 180px;
    border-left: var(--door-border);
    border-top: var(--door-border);
    border-right: var(--door-border);
    display: flex;
    justify-content: center;
    align-items: flex-end;
}
.door {
    position: absolute;
    top: 5px;
    height: 295px;
    width: 170px;
    background: linear-gradient(to top, rgb(184, 94, 30), rgb(138, 67, 17));
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 15px;
}
.door .knob {
    height: 20px;
    width: 20px;
    border-radius: 10px;
    background: radial-gradient( rgb(223, 223, 223), rgb(124, 124, 124));
    align-self: flex-start;
    margin-top: 60px;
}
.door-frame.selected {
    border-left: var(--selected-border);
    border-top: var(--selected-border);
    border-right: var(--selected-border);
}
.door > .number.selected {
    color: yellow;
}
.door.open {
    background: rgba(0, 0, 0, 0.7);
}
.door.open .knob {
    display: none;
}
.door.open .number {
    display: none;
}
</style>