<template>
	<button class="btn">
		<slot></slot>
	</button>
</template>

<script>
export default {
	name: "my-buttons",
};
</script>

<style scoped>
.btn {
	border: 1px;
	cursor: pointer;
}
</style>