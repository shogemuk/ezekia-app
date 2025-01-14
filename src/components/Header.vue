<template>
	<header>
		<img src="/assets/img/nhm-logo.png" alt="logo" />

		<button type="menu"></button>
	</header>
</template>

<script>
export default {
	name: "AppHeader",
};
</script>

<style lang="scss" scoped>
header {
	$color-black: #000;

	background: #e0e0e0;
	height: 127px;
	margin: 0;
	display: flex;
	align-items: center;
	justify-content: space-between;
	padding: 0 53px;

	button {
		width: 60px;
		height: 13px;
		position: relative;
		border: none;
		border-radius: 13px;
		background: $color-black;

		background-size: 10px 100%;
		&:before,
		&:after {
			content: "";
			height: 13px;
			width: 49px;
			background: $color-black;
			left: 0;
			border-radius: 13px;
			position: absolute;
		}
		&:before {
			top: -20px;
		}
		&:after {
			bottom: -20px;
		}
	}
}
</style>
