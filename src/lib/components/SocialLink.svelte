<script lang="ts">
	import type { Component } from "svelte";

	interface Props {
		icon: any;
		name: string;
		href: string;
	}

	const { icon: Icon, name, href }: Props = $props();
</script>

<a
	class="social"
	{href}
	target="_blank"
	rel="noopener noreferrer"
	aria-label={name}
	title={name}
>
	<Icon size={24} />
</a>

<style>
	.social {
		width: 52px;
		height: 52px;

		display: flex;
		align-items: center;
		justify-content: center;

		border-radius: 999px;

		color: white;
		text-decoration: none;

		background: rgba(255, 255, 255, 0.08);
		border: 1px solid rgba(255, 255, 255, 0.12);
		backdrop-filter: blur(12px);

		transition:
			transform 0.2s ease,
			background-color 0.2s ease,
			box-shadow 0.2s ease;
	}

	.social:hover {
		transform: scale(1.12);

		background: rgba(255, 255, 255, 0.16);

		box-shadow: 0 0 18px rgba(255, 255, 255, 0.18);
	}

	.social:active {
		transform: scale(1.04);
	}

	.social:focus-visible {
		outline: 2px solid white;
		outline-offset: 4px;
	}
</style>
