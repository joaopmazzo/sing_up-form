<template>
	<aside>
		<div class="wrapper">
			<h1>Learn to code by watching others</h1>
			<p>See how experienced developers solve problems in real-time. Watching scripted tutorials is great, but understanding how developers think is invaluable.</p>
		</div>
	</aside>
</template>

<script>
export default {
	name: "AsideComponent",
}
</script>

<style scoped>
aside {
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: flex-end;
}

.wrapper {
	max-width: 38vw;
}

h1 {
	font-size: var(--big-header);
	font-weight: var(--bold);
	line-height: 55px;

	margin-bottom: 11px;
}

p {
	font-size: var(--normal);
	font-weight: var(--medium);
	line-height: 26px;
}

@media (max-width:  920px) {
	aside {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.wrapper {
		min-width: 70vw;
	}

	h1 {
		font-size: var(--small-header);
		line-height: 36px;

		text-align: center;
	}

	p {
		text-align: center;
	}
}

@media (max-width:  640px) {
	aside {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.wrapper {
		min-width: 90vw;
	}

	h1 {
		font-size: var(--small-header);
		line-height: 36px;

		text-align: center;
	}

	p {
		text-align: center;
	}
}
</style>