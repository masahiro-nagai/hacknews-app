<script context="module">
    // 93717e45b2d24be383834ddabebd370d
    //Input
    export async function load({fetch}){
        const response = await fetch('https://jsonplaceholder.typicode.com/posts');
        return{
            props: {
                posts: response.ok && (await response.json())
            }
        };
    }

</script>

<script>
    //propsの値を受け取る
    export let posts;
</script>
<!-- 記事一覧(配列)なので、eachで走査してあげる -->
<ul class="post-list">
    {#each posts as post}
        <!-- 詳細ページへのリンク -->
        <li><a href={`posts/${post.id}`} class="post-link">{post.title}</a></li>
    {/each}
</ul>
<style>
	.post-list {
		list-style-type: decimal;
	}

	.post-list > li {
		margin-top: 10px;
	}

	.post-link {
		color: #000;
		text-decoration: none;
	}

	.post-link:hover {
		text-decoration: underline;
	}
</style>