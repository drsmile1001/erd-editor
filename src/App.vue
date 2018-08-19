<template>
    <el-container>
    <el-aside width="200px">
        <main-menu/>
    </el-aside>
    <el-main>
        <editor/>
    </el-main>
    </el-container>
</template>

<script>
import editor from "./components/editor"
import menu from "./components/menu"

export default {
   components:{
       editor,
       "main-menu":menu
   }
}
</script>

<style>


</style>
