<script lang="ts">
	import { onMount } from 'svelte';
	import { page } from '$app/stores';
	import { GraphQLClient, gql } from 'graphql-request';

	// type Post = {
	// 	title: any;
	// 	description: any;
	// 	image: any;
	// 	slug: any;
	// 	body: {};
	// };

	let slugID = $page.params.slug;
	let blog: any;

	onMount(() => main(false));
	export async function main(wait: boolean) {
		const endpoint = '';

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
						body
					}
				}
			}
		`;
		await graphQLClient.request(query).then((res) =>
			setTimeout(
				() => {
					blog = JSON.stringify(
						res.listSvelteBlogs.data.find((p: { slug: string }) => p.slug === slugID)
					);
				},
				// Simulate a long load time.
				wait ? 2000 : 0
			)
		);
	}

	// Fetch Error
	main(false).catch((error) => console.error(error));
</script>

<svelte:head>
	<title>Blog details</title>
	<meta name="description" content="Svelte blog app" />
</svelte:head>

<section>
	<pre>{blog}</pre>
	<a href="/"><button class="btn btn-primary">Go Back</button></a>
	<div class="card-wrapper">
		<div class="card">
			<div class="card-header">
				<img
					src="https://images.unsplash.com/photo-1646974005583-01e9a7b0b5f8?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=876&q=80"
					alt=""
				/>
			</div>
			<div class="card-content">
				<span>Technology</span>
				<h3>{blog}</h3>
				<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid, temporibus!</p>
			</div>
		</div>
	</div>
</section>

<style>
	.btn {
		appearance: none;
		-webkit-appearance: none;
		font-family: sans-serif;
		cursor: pointer;
		padding: 12px;
		min-width: 100px;
		border: 0px;
		-webkit-transition: background-color 100ms linear;
		-ms-transition: background-color 100ms linear;
		transition: background-color 100ms linear;
	}
	.btn-primary {
		background: #3498db;
		color: #ffffff;
	}

	.btn-primary:hover {
		background: #2980b9;
		color: #ffffff;
	}
	.btn:focus {
		outline: 0;
	}

	.card-wrapper {
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.card {
		width: 860px;
		background-color: #fff;
		box-shadow: 0 0 7px rgba(0, 0, 0, 0.6);
		border-radius: 0.5rem;
	}

	.card-header {
		width: 100%;
	}

	.card-header img {
		width: 100%;
		border-top-left-radius: 0.5rem;
		border-top-right-radius: 0.5rem;
	}

	.card-content {
		padding: 1rem;
	}

	.card-content span {
		background-color: #51adc4;
		color: #fff;
		font-weight: 300;
		font-size: 10px;
		padding: 0.5rem 0.75rem;
		border-radius: 1rem;
		text-transform: uppercase;
	}

	.card-content h3 {
		margin: 1rem 0 0.5rem 0;
	}

	.card-content p {
		font-size: 14px;
	}

	.card-footer {
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 1rem;
	}
</style>
