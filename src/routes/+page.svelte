<script lang="ts">
	import { onMount } from 'svelte';
	import Card from '../component/Card.svelte';

	// type Post = {
	// 	createdAt: Date;
	// 	image: any;
	// 	content: string;
	// 	title: string;
	// 	id: number;
	// };

	// let items: Post[] = [];
	// let loaded = false;

	// onMount(() => loadThings(false));

	// function loadThings(wait: boolean) {
	// 	if (typeof fetch !== 'undefined') {
	// 		loaded = false;

	// 		fetch('https://api.fake-rest.refine.dev/posts')
	// 			.then((response) => response.json())
	// 			.then((json) =>
	// 				setTimeout(
	// 					() => {
	// 						items = json;
	// 						loaded = true;
	// 					},
	// 					// Simulate a long load time.
	// 					wait ? 2000 : 0
	// 				)
	// 			);
	// 	}
	// }

	// import { request, gql } from 'graphql-request';

	// const query = gql`
	// 	{
	// 		listContentModels {
	// 			data {
	// 				name
	// 				modelId
	// 			}
	// 		}
	// 	}
	// `;

	// let data: any = [];

	// onMount(() => loadData(false));

	// const endpoint = import.meta.env.VITE_PUBLIC_CMS_ENPOINT;
	// const secret = import.meta.env.VITE_PUBLIC_TOKEN_SECRET;
	// function loadData(wait: boolean) {
	// 	request(`https://d3ats32nbrgv3r.cloudfront.net/cms/read/en-US`, query).then((data) =>
	// 		console.log(data)
	// 	);
	// 	// Simulate a long load time.
	// 	wait ? 2000 : 0;
	// }

	// import { GraphQLClient, gql } from 'graphql-request';

	// const query = gql`
	// 	{
	// 		countries {
	// 			name
	// 			emoji
	// 		}
	// 	}
	// `;

	// export const load = async () => {
	// 	const graphCMSClient = new GraphQLClient('https://countries.trevorblades.com/', {
	// 		headers: {}
	// 	});

	// 	const { countries } = await graphCMSClient.request(query);

	// 	return {
	// 		props: { countries }
	// 	};
	// }

	import { GraphQLClient, gql } from 'graphql-request';

	let blog: any[];
	let loading = false;

	onMount(() => main(false));
	export async function main(wait: boolean) {
		const endpoint = '';

		loading = false;
		const graphQLClient = new GraphQLClient(endpoint, {
			headers: {
				authorization: 'Bearer '
			}
		});

		const query = gql`
			{
				listSvelteBlogs {
					data {
						title
						description
						image
						slug
					}
				}
			}
		`;
		await graphQLClient.request(query).then((res) =>
			setTimeout(
				() => {
					blog = res.listSvelteBlogs.data;
					loading = true;
				},
				// Simulate a long load time.
				wait ? 2000 : 0
			)
		);
		console.log(JSON.stringify(blog, null, 2));
	}

	// Fetch Error
	main(false).catch((error) => console.error(error));
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte blog app" />
</svelte:head>

<section>
	<h1>
		<span class="welcome">Create a blog with Webiny and Svelte / SvelteKit </span>
	</h1>

	<Card {blog} {loading} />
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 1;
	}

	.welcome {
		text-align: center;
	}
	h1 {
		margin-bottom: 3rem;
	}
</style>
