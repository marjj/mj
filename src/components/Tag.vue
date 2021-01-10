<template>
	<div :class="cls" :key=1>
		<i class="bracket">&lt;</i>
		<i class="tag">{{content}}</i>
		<i class="bracket">&gt;</i>
		<slot></slot>
		<i class="bracket">&lt;</i>
		<i class="tag">{{content}}</i>
		<i class="bracket">/&gt;</i>
	</div>
</template>

<script type="text/javascript">
export default {
	props: ['content', 'cls']
}
</script>

<style lang="scss" scoped>
i {
  text-transform: none;
  text-decoration: none;
  font-style: normal;
}
div {
	position: relative;
	z-index: -1;
	&.parent:after {
		position: absolute;
		content: '';
		width: 1px;
		height: 90%;
		top: 5%;
		left:0 ;
		background: rgba(255, 255, 255, 0.2)
	}
}
.bracket {
  color: #86d7dc
}
.tag {
  color: #ff4f7f
}
.tabbed {
	margin-left: 20px
}
</style>