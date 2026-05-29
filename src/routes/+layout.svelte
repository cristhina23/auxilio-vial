<script>
	import './layout.css';
	import favicon from '/icon.png';

	import {
		seoConfig,
		businessInfo,
	} from '../../data/site.js';

	let { children } = $props();

	const siteUrl =
		'https://rescatevialexpress.com';

	const ogImage =
		`${siteUrl}/shareable.png`;
</script>

<svelte:head>
	<title>{seoConfig.title}</title>

	<link
		rel="icon"
		href='/icon.png'
	/>

	<meta
		name="description"
		content={seoConfig.description}
	/>

	<meta
		name="keywords"
		content={seoConfig.keywords.join(', ')}
	/>

	<meta
		name="author"
		content={seoConfig.author}
	/>

	<meta
		name="robots"
		content="index,follow"
	/>

	<meta
		name="theme-color"
		content="#e50914"
	/>

	<link
		rel="canonical"
		href={siteUrl}
	/>

	<!-- OPEN GRAPH -->

	<meta
		property="og:type"
		content="website"
	/>

	<meta
		property="og:title"
		content={seoConfig.title}
	/>

	<meta
		property="og:description"
		content={seoConfig.description}
	/>

	<meta
		property="og:url"
		content={siteUrl}
	/>

	<meta
		property="og:image"
		content={ogImage}
	/>

	<meta
		property="og:image:width"
		content="1200"
	/>

	<meta
		property="og:image:height"
		content="630"
	/>

	<meta
		property="og:site_name"
		content={businessInfo.name}
	/>

	<meta
		property="og:locale"
		content="es_PE"
	/>

	<!-- TWITTER -->

	<meta
		name="twitter:card"
		content="summary_large_image"
	/>

	<meta
		name="twitter:title"
		content={seoConfig.title}
	/>

	<meta
		name="twitter:description"
		content={seoConfig.description}
	/>

	<meta
		name="twitter:image"
		content={ogImage}
	/>

	<!-- LOCAL SEO -->

	<meta
		name="geo.region"
		content="PE-LMA"
	/>

	<meta
		name="geo.placename"
		content="Lima"
	/>
</svelte:head>

{@render children()}