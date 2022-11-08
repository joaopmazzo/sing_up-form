<template>
	<main>
		<aside-component-text />
		<sing-up-form />
	</main>
</template>

<script>
import SingupForm from "../components/SingupForm.vue";
import AsideComponent from "../components/AsideComponent.vue";

export default {
	components: {
		"sing-up-form": SingupForm,
		"aside-component-text": AsideComponent,
	},
	name: "Singup",
};
</script>

<style scoped>
main {
	min-height: 100vh;

	display: grid;
	grid-template-columns: 1fr 1fr;
	gap: 45px;
}

@media (max-width:  920px) {
	main {
		grid-template-columns: 1fr;

		margin: 88px 0px 68px 0px;
	}
}
</style>