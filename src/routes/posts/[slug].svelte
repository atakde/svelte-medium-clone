<script context="module">
	export async function load({ fetch, params }) {
		const slug = params.slug;
		const response = await fetch(`https://dummyjson.com/posts/${slug}`);
		const post = await response.json();

		if (response.status === 200) {
			const img = '<img src="https://dummyimage.com/600x400/000/fff" alt="">';
			return {
				props: {
					post: {
						...post,
						body: img + '<p>' + post.body + '</p>'
					}
				}
			};
		}

		return {
			status: response.status,
			error: new Error('Failed to load post')
		};
	}
</script>

<script>
	export let post;
</script>

<svelte:head>
	<title />
	<meta name="description" content="" />
</svelte:head>

<section>
	<h1>{post.title}</h1>
	<div class="post-information">
		<div class="author-container">
			<img
				width="32"
				src="https://atakann.com/static/media/img-profile.e1ab5d54becc4acc26c5.jpeg"
				alt="Author"
			/>
			<div>
				<div class="author-name">Atakan Demircioğlu</div>
				<div class="post-date">
					<span>Aug 21, 2022</span>
					<span>1 min read</span>
				</div>
			</div>
		</div>
		<div class="social-container">
			<a href="/">
				<svg
					width="20"
					height="17"
					viewBox="0 0 20 17"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						d="M20 1.92375C19.2563 2.25 18.4637 2.46625 17.6375 2.57125C18.4875 2.06375 19.1363 1.26625 19.4412 0.305C18.6488 0.7775 17.7738 1.11125 16.8412 1.2975C16.0887 0.49625 15.0162 0 13.8462 0C11.5763 0 9.74875 1.8425 9.74875 4.10125C9.74875 4.42625 9.77625 4.73875 9.84375 5.03625C6.435 4.87 3.41875 3.23625 1.3925 0.7475C1.03875 1.36125 0.83125 2.06375 0.83125 2.82C0.83125 4.24 1.5625 5.49875 2.6525 6.2275C1.99375 6.215 1.3475 6.02375 0.8 5.7225C0.8 5.735 0.8 5.75125 0.8 5.7675C0.8 7.76 2.22125 9.415 4.085 9.79625C3.75125 9.8875 3.3875 9.93125 3.01 9.93125C2.7475 9.93125 2.4825 9.91625 2.23375 9.86125C2.765 11.485 4.2725 12.6788 6.065 12.7175C4.67 13.8088 2.89875 14.4662 0.98125 14.4662C0.645 14.4662 0.3225 14.4513 0 14.41C1.81625 15.5813 3.96875 16.25 6.29 16.25C13.835 16.25 17.96 10 17.96 4.5825C17.96 4.40125 17.9538 4.22625 17.945 4.0525C18.7588 3.475 19.4425 2.75375 20 1.92375Z"
						fill="#292929"
					/>
				</svg>
			</a>
			<a href="/">
				<svg
					width="20"
					height="20"
					viewBox="0 0 20 20"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						d="M18.5576 0H1.44241C0.645752 0 0 0.645752 0 1.44241V18.5576C0 19.3542 0.645752 20 1.44241 20H18.5576C19.3542 20 20 19.3542 20 18.5576V1.44241C20 0.645752 19.3542 0 18.5576 0V0ZM7.09412 15.1172H4.65866V7.79007H7.09412V15.1172ZM5.87646 6.78955H5.8606C5.04333 6.78955 4.51477 6.22696 4.51477 5.52383C4.51477 4.80484 5.05951 4.25781 5.89264 4.25781C6.72577 4.25781 7.23846 4.80484 7.25433 5.52383C7.25433 6.22696 6.72577 6.78955 5.87646 6.78955ZM15.8759 15.1172H13.4407V11.1974C13.4407 10.2122 13.0881 9.54041 12.2069 9.54041C11.5341 9.54041 11.1334 9.99359 10.9573 10.4311C10.8929 10.5876 10.8772 10.8064 10.8772 11.0254V15.1172H8.44193C8.44193 15.1172 8.47382 8.47748 8.44193 7.79007H10.8772V8.82751C11.2009 8.32825 11.7799 7.6181 13.0721 7.6181C14.6744 7.6181 15.8759 8.66531 15.8759 10.9158V15.1172Z"
						fill="#292929"
					/>
				</svg>
			</a>
			<a href="/">
				<svg
					width="24"
					height="24"
					viewBox="0 0 24 24"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						d="M20.896 2H3.10303C2.49377 2.00037 1.99988 2.49451 2 3.104V20.897C2.00037 21.5062 2.49451 22.0001 3.104 22H12.6836V14.2656H10.0859V11.2383H12.6836V9.01038C12.6836 6.42676 14.2609 5.02051 16.5656 5.02051C17.6694 5.02051 18.618 5.10278 18.8945 5.13953V7.83984H17.3053C16.0514 7.83984 15.8086 8.43567 15.8086 9.31018V11.2383H18.8066L18.416 14.2656H15.8086V22H20.896C21.5056 22.0001 21.9999 21.5061 22 20.8965C22 20.8964 22 20.8962 22 20.896V3.10303C21.9998 2.49377 21.5055 1.99988 20.896 2Z"
						fill="#292929"
					/>
				</svg>
			</a>
			<a href="/">
				<svg
					width="24"
					height="24"
					viewBox="0 0 24 24"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						d="M19.6625 2.66111C19.4906 2.41419 19.2591 2.23363 18.9685 2.11908C18.7834 2.03986 18.5895 2.00019 18.3867 2.00019V2H4.5333C4.33064 2 4.13688 2.03968 3.95178 2.1189C3.66102 2.23335 3.42961 2.41415 3.25779 2.66092C3.08602 2.9077 3 3.18077 3 3.48047V20.5195C3 20.8193 3.08602 21.0923 3.25779 21.3393C3.42961 21.586 3.66102 21.7668 3.95178 21.8812C4.1367 21.9604 4.33064 22 4.5333 22C4.94763 22 5.31316 21.8545 5.6305 21.564L11.4601 15.9589L17.2896 21.5641C17.5981 21.8456 17.9638 21.9867 18.3867 21.9867C18.6071 21.9867 18.801 21.9517 18.9684 21.8811C19.259 21.7667 19.4905 21.586 19.6624 21.3389C19.8342 21.0923 19.92 20.8192 19.92 20.5195V3.48065C19.9201 3.18096 19.834 2.90788 19.6625 2.66111ZM18.2281 20.1095L12.6366 14.7427L11.4601 13.6193L10.2836 14.7427L4.69215 20.1095V3.6922H18.2281V20.1095Z"
						fill="#292929"
					/>
				</svg>
			</a>
			<a href="/">
				<svg
					width="24"
					height="24"
					viewBox="0 0 24 24"
					fill="none"
					xmlns="http://www.w3.org/2000/svg"
				>
					<path
						d="M19.1891 9C17.6368 8.99982 16.3783 10.2584 16.3783 11.8109C16.3783 13.3632 17.6368 14.6217 19.1891 14.6217C20.7416 14.6217 22 13.3632 22 11.8109C21.9982 10.2591 20.7409 9.00176 19.1891 9ZM19.1891 13.5011C18.2558 13.5011 17.4989 12.7442 17.4989 11.8109C17.4989 10.8775 18.2558 10.1208 19.1891 10.1208C20.1225 10.1208 20.8792 10.8773 20.8792 11.8109C20.8782 12.7439 20.122 13.4996 19.1891 13.5011Z"
						fill="#292929"
					/>
					<path
						d="M12.0002 9C10.4477 9 9.18909 10.2584 9.18909 11.8109C9.18909 13.3632 10.4477 14.6217 12.0002 14.6217C13.5525 14.6217 14.8109 13.3632 14.8109 11.8109C14.8109 10.2584 13.5525 9 12.0002 9ZM12.0002 13.5011C11.0665 13.5011 10.3097 12.7442 10.3097 11.8109C10.3097 10.8773 11.0665 10.1208 12.0002 10.1208C12.9335 10.1208 13.6901 10.8773 13.6901 11.8109C13.6901 12.7442 12.9335 13.5011 12.0002 13.5011Z"
						fill="#292929"
					/>
					<path
						d="M4.81092 9C3.25843 9 2 10.2584 2 11.8109C2 13.3632 3.25843 14.6217 4.81092 14.6217C6.36324 14.6217 7.62166 13.3632 7.62166 11.8109C7.61991 10.2591 6.36253 9.00176 4.81092 9ZM4.81092 13.5011C3.87746 13.5011 3.12079 12.7442 3.12079 11.8109C3.12079 10.8773 3.87746 10.1208 4.81092 10.1208C5.74438 10.1208 6.50088 10.8773 6.50088 11.8109C6.50088 12.7442 5.74421 13.5011 4.81092 13.5011Z"
						fill="#292929"
					/>
				</svg>
			</a>
		</div>
	</div>
	<div class="content">
		{@html post.body}
	</div>
	<div class="tags">
		{#each post.tags as tag}
			<a href="/tag/{tag}">{tag}</a>
		{/each}
	</div>
	<div class="written-container">
		<img src="https://atakann.com/static/media/img-profile.e1ab5d54becc4acc26c5.jpeg" alt="Author"/>
		<div>
			<span class="written-by">Written by</span>
			<a href="/author/">Atakan Demircioğlu</a>
			<small>Some information about writer</small>
		</div>
	</div>
</section>

<style lang="scss">
	section {
		font-family: 'Georgia';
		margin-top: 33px;
	}

	h1 {
		font-weight: 400;
		font-size: 39px;
		line-height: 44px;
		color: #292929;
	}

	.post-information {
		margin-top: 23px;
		display: flex;
		font-family: 'Segoe UI';
		justify-content: space-between;
		align-items: center;
	}

	.post-information > div {
		display: flex;
	}

	.author-container {
		gap: 10px;
		align-items: center;
	}

	.author-name {
		font-size: 14px;
		font-weight: 500;
		color: #292929;
	}

	.post-date {
		font-size: 14px;
		line-height: 19px;
		font-weight: 600;
		color: #757575;
	}

	.post-information > div > img {
		width: 50px;
		height: 50px;
		border-radius: 50%;
	}

	.social-container {
		gap: 12px;
		align-items: center;
		justify-content: center;
	}

	.social-container > a {
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.content {
		margin-top: 56px;
		display: flex;
		flex-direction: column;
		gap: 24px;
	}

	.tags {
		margin-top: 30px;
		display: flex;
		font-family: 'Segoe UI';
	}

	.tags > a {
		padding: 5px 10px;
		background: #F2F2F2;
		border-radius: 4px;
		color: #777777;
		margin-right: 10px;
		font-size: 13px;
		font-weight: 400;
		text-decoration: none;
	}

	.written-container {
		font-family: 'Segoe UI';
		margin-top: 30px;
		display: flex;
		gap: 17px;
		padding: 28px 0;
		border-top: 1px solid #ddd;
		border-bottom: 1px solid #ddd;
	}

	.written-container > img {
		width: 85px;
		height: 85px;
		border-radius: 50%;
	}

	.written-container > div {
		gap: 6px;
		display: flex;
		flex-direction: column;
	}

	.written-container > div > a {
		font-size: 25px;
		font-weight: 700;
		color: #292929;
		text-decoration: none;
	}
	
	.written-container > div > small {
		font-size: 16px;
		font-weight: 400;
		color: #757575;
	}

	.written-by {
		font-size: 14px;
		font-weight: 400;
		color: #757575;
	}

</style>
