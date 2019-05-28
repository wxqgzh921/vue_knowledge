<template>
	<div class="is">
		<h1>{{msg}}</h1>
		<div is="h3">fdjfjfp</div>
		<div>
			<slot :username= "userName">
				<!-- {{ userName}} -->
				2313123
			</slot>
		</div>
	</div>
</template>

<script>
	export default{
		name:'is_one',
		data(){
			return {
				msg:'这是第一个子组件',
				userName: {
					fristname:'丑',
					lastname:'八怪'
				}
			}
		}
	}
</script>