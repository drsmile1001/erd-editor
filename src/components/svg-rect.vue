<template>
    <g :transform="transform">
        <rect fill="#FF6CC4"
              stroke="#C30D23"
              stroke-width="3"
              width="75"
              height="75">
            
        </rect>
        <text font-size="14"
              text-anchor="middle">
            <tspan>Employee</tspan>
        </text>
    </g>
</template>

<script>
export default {
    props: {
        x: Number,
        y: Number
    },
    computed:{
        transform(){
            return `translate(${this.x},${this.y})`
        }
    }
}
</script>

<style>
</style>
