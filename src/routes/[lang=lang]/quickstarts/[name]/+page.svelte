<script type="ts">
	import { Breadcrumbs } from '@emerald-dao/component-library';
	import Sidebar from '../__components/Sidebar.svelte';
	import { page } from '$app/stores';
	import LL from '$i18n/i18n-svelte';
	import { ContentTypeEnum } from '$lib/types/content/metadata/content-types.enum';

	export let data;

	$: routes = [
		{
			path: `/${$page.params.lang}/quickstarts`,
			label: $LL[ContentTypeEnum.Quickstart]()
		},
		{
			path: `/${$page.params.lang}/quickstarts/${$page.params.name}`,
			label: `${data.overview.title}`
		}
	];
</script>

<section class="container-medium">
	<div class="main-wrapper">
		<Breadcrumbs {routes} />
		<div class="template">&lt/&gt Quickstart</div>
		<article>
			<h1 class="heading w-medium">{data.overview.title}</h1>
			<p class="w-medium">{data.overview.description}</p>
			<div class="readme-wrapper">
				<svelte:component this={data.readme} />
			</div>
		</article>
	</div>
	<Sidebar {data} />
</section>

<style type="scss">
	section {
		display: flex;
		flex-direction: column;
		gap: var(--space-7);

		@include mq(medium) {
			display: grid;
			grid-template-columns: 1fr 2fr !important;
			gap: var(--space-10);
		}

		.main-wrapper {
			.template {
				width: fit-content;
				color: var(--clr-primary-main);
				background-color: var(--clr-primary-badge);
				border: var(--border-width-primary) var(--clr-primary-main) solid;
				border-radius: var(--radius-2);
				padding: var(--space-3) var(--space-4);
				margin-top: var(--space-6);
				font-size: var(--font-size-1);
			}

			article {
				margin-top: var(--space-6);
				max-width: 85ch;

				.readme-wrapper {
					border: var(--border-width-primary) var(--clr-border-primary) solid;
					border-radius: var(--space-5);
					padding: var(--space-5);
					word-break: break-word;

					@include mq(medium) {
						padding: var(--space-10);
					}
				}
			}
		}
	}
</style>
