<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte blog app" />
</svelte:head>

<section>
	<h1>
		<span class="welcome">Welcome Back</span>
	</h1>

	<main class="container">
		<div class="card-container">
			<div class="card-image">
				<img
					src="https://images.unsplash.com/photo-1542362567-b07e54358753?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80"
					alt="a brand new sports car"
				/>
			</div>
			<div class="card-body">
				<span class="card-badge card-badge-blue">Car design</span>
				<h1>Why is the sports cars so well designed?</h1>
				<p class="card-subtitle">An exploration into the car design industry and how it works</p>
				<div class="card-author">
					<img
						src="https://images.unsplash.com/photo-1542362567-b07e54358753?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80"
						alt="author avatar"
					/>
					<div class="author-info">
						<p class="author-name">John Doe</p>
						<p class="post-timestamp">2h ago</p>
					</div>
				</div>
			</div>
		</div>

		<div class="card-container">
			<div class="card-image">
				<img
					src="https://images.unsplash.com/photo-1504728078670-d0a59873c8c4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80"
					alt="a landscape view full of baloons"
				/>
			</div>
			<div class="card-body">
				<span class="card-badge card-badge-purple">Adventure</span>
				<h1>Discover new adventures over the world</h1>
				<p class="card-subtitle">Adventure and baloons are trends these days</p>
				<div class="card-author">
					<img
						src="https://images.unsplash.com/photo-1504728078670-d0a59873c8c4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80"
						alt="author avatar"
					/>
					<div class="author-info">
						<p class="author-name">John Doe</p>
						<p class="post-timestamp">2h ago</p>
					</div>
				</div>
			</div>
		</div>

		<div class="card-container">
			<div class="card-image">
				<img
					src="https://images.unsplash.com/photo-1506422748879-887454f9cdff?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80"
					alt="a city full of buildings"
				/>
			</div>
			<div class="card-body">
				<span class="card-badge card-badge-pink">Engineering</span>
				<h1>Living in downtown in the biggest cities</h1>
				<p class="card-subtitle">
					Citizens of the biggest cities in the world talk about their lives
				</p>
				<div class="card-author">
					<img
						src="https://images.unsplash.com/photo-1506422748879-887454f9cdff?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80"
						alt="author avatar"
					/>
					<div class="author-info">
						<p>John Doe</p>
						<p>2h ago</p>
					</div>
				</div>
			</div>
		</div>
	</main>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 1;
	}

	h1 {
		width: 100%;
	}

	.container {
		display: grid;
		grid-template-columns: 1fr 1fr 1fr;
		gap: 20px;
	}

	.card-container {
		width: 350px;
		height: 440px;
		background-color: #fff;
		border-radius: 8px;
		margin: auto;
		box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
		overflow: hidden;
	}

	.card-image img {
		height: 220px;
		width: 100%;
		border-radius: 8px 8px 0 0;
		background-size: cover;
	}

	.card-body {
		display: flex;
		flex-direction: column;
		align-items: start;
		padding: 16px;
		min-height: 200px;
	}

	.card-badge {
		text-transform: uppercase;
		background-color: #fff;
		color: #fff;
		padding: 2px 8px;
		border-radius: 70px;
		margin: 0;
		font-size: 12px;
	}

	.card-badge-blue {
		background-color: #92d4e4;
	}

	.card-badge-purple {
		background-color: #3d1d94;
	}

	.card-badge-pink {
		background-color: #c62bcb;
	}

	.card-body h1 {
		font-size: 16px;
		margin: 8px 0;
	}

	.card-body p {
		font-size: 14px;
		margin: 8px 0 16px 0;
	}

	.card-author {
		display: flex;
		align-items: center;
	}

	.card-author p {
		margin: 0 16px;
		font-size: 12px;
	}

	.card-author p:last-child {
		color: #888;
	}

	.card-author img {
		border-radius: 50%;
		height: 48px;
		width: 48px;
		margin-top: auto;
	}

	@media screen and (max-width: 1000px) {
		.container {
			grid-template-columns: 1fr;
		}
	}
</style>
