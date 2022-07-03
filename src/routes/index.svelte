<script context="module">
	export async function load({ fetch }) {
		const response = await fetch('https://dummyjson.com/posts?limit=10');
		const data = await response.json();

		if (response.status === 200) {
			return {
				props: {
					posts: data.posts
				}
			};
		}

		return {
			status: response.status,
			error: new Error('Failed to load posts')
		};
	}
</script>

<script>
	export let posts;
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte medium clone" />
</svelte:head>

<section>
	{#each posts as post}
		<article>
			<a href="/posts/{post.id}">
				<div class="author">
					<img
						width="32"
						src="https://atakann.com/static/media/img-profile.e1ab5d54becc4acc26c5.jpeg"
						alt="Author"
					/>
					<span>Atakan Demircioğlu</span>
					<span>2 days ago</span>
				</div>
				<h2>{post.title}</h2>
				<div>{post.body}</div>
				<div class="article-footer">
					<span class="tag">Javascript</span>
					<span>4 min read</span>
					<span>Selected for you</span>
				</div>
			</a>
		</article>
	{/each}
</section>

<style lang="css">
	h2 {
		font-size: 22px;
		font-weight: 700;
		padding: 0;
		margin: 0;
	}

	article {
		font-family: 'Roboto', sans-serif;
		font-size: 14px;
	}

	article > a {
		text-decoration: none;
		color: rgba(41, 41, 41, 1);
		display: flex;
		flex-direction: column;
		gap: 10px;
		padding: 24px 0;
		border-bottom: 1px solid rgb(231, 228, 228);
	}

	.author {
		display: flex;
		align-items: center;
		gap: 6px;
	}

	.author > span {
		font-size: 14px;
		font-weight: 400;
	}

	.author > span:last-child {
		color: #757575;
	}

	.author > img {
		width: 24px;
		height: 24px;
		border-radius: 50%;
	}

	.article-footer {
		display: flex;
		align-items: center;
		gap: 8px;
		font-size: 13px;
		color: rgba(117, 117, 117, 1);
	}

	.tag {
		background-color: rgba(242, 242, 242, 1);
		color: rgba(41, 41, 41, 1);
		padding: 6px;
		border-radius: 100px;
	}
</style>
