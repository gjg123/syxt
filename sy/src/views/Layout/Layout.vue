<template>
	<div class="layout">
		<top-nav></top-nav>
		<div class="container">
			<home></home>
		</div>
	</div>
</template>

<script>
	import topNav from '../../components/topNav/topNav.vue'
	import Home from '../Home/Home.vue'
	export default {
		components:{
			topNav,
			Home
		}
	}
</script>

<style scoped>
	.layout{
		width:100%;
		height:100%;
		background: #f0f0f0;
	}
	.container{
		width:80%;
		margin: auto;
		height:calc(100% - 50px);
	}
</style>