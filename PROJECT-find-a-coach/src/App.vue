<!-- 
    theme-color:#0ca678
    darker:#087f5b
    lighter:#96f2d7 #e6fcf5

    lighter lighter:#d3f9d8

    second:#f59f00
    darker:#e67700
    lighter:#ffec99

    third:#4263eb
    darker:#364fc7
    lighter:#bac8ff

    grey:#495057
    darker:#212529
    lighter:#e9ecef
    /*
    SPACING SYSTEM (px)
    2 / 4 / 8 / 12 / 16 / 24 / 32 / 48 / 64 / 80 / 96 / 128

    FONT SIZE SYSTEM (px)
    10 / 12 / 14 / 16 / 18 / 20 / 24 / 30 / 36 / 44 / 52 / 62 / 74 / 86 / 98
    */
 -->

<template>
	<the-header></the-header>
	<router-view></router-view>
</template>

<script>
import TheHeader from './components/layout/TheHeader.vue';

export default {
	components: {
		TheHeader,
	},
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@500;600;700&family=Noto+Sans+SC:wght@400;500;700&display=swap');

* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}

html {
	font-family: 'Inter', 'Noto Sans SC', sans-serif;
	font-size: 62.5%;
}
</style>
