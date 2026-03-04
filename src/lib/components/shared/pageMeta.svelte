<script lang="ts">
	import { page } from "$app/state";
	// VARIABLES
	const { title, description, ogType = "website", image = "https://svelte0.com/images/og.png" }: Props = $props();
	const fullPageTitle = $derived(title ? `${title} | Svelte0` : "Svelte0");
	const pageDescription = $derived(description || "Generate svelte projects using AI.");
	// Props type
	interface Props {
		title?: string | undefined;
		ogType?: "website" | "article";
		description?: string;
		image?: string;
	}
</script>

<svelte:head>
	<link rel="icon" href="https://svelte0.com/images/favicon.png" />
	<!-- Primary Meta Tags -->
	<title>{fullPageTitle}</title>
	<meta name="title" content={fullPageTitle} />
	<meta name="description" content={pageDescription} />
	<!-- Open Graph / Facebook -->
	<meta property="og:type" content={ogType} />
	<meta property="og:url" content={page.url.href} />
	<meta property="og:title" content={fullPageTitle} />
	<meta property="og:description" content={pageDescription} />
	<meta property="og:image" content={image} />
	<!-- Twitter -->
	<meta property="twitter:card" content="summary_large_image" />
	<meta property="twitter:url" content={page.url.href} />
	<meta property="twitter:title" content={fullPageTitle} />
	<meta property="twitter:description" content={pageDescription} />
	<meta property="twitter:image" content={image} />
</svelte:head>
