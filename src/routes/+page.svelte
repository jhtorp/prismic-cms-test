<script>
	import createClient from '$lib/prismicio';
	import * as prismicH from '@prismicio/helpers';

	const client = createClient();
	const prismicQuery = client.getFirst();

	export let data;

	$: posts = data.document;

	$: console.log(posts[0].data);
</script>

<!-- {#await prismicQuery}
	<p>Loading...</p>
{:then prismicResponse}
	<h1>{prismicH.asText(prismicResponse.data.title)}</h1>
	{@html prismicH.asHTML(prismicResponse.data.content)}
{:catch error}
	<pre>{error.message}</pre>
{/await} -->

{#each posts as post}
	<div class="post">
		<h1>{post.data.title[0].text}</h1>
		<p>{post.data.content[0].text}</p>
	</div>
{/each}
