<script context="module">
    export const prerender = true;

    export async function load({ page, fetch, session, context }) {
        let res = await fetch('/posts/recent-posts.json');

        return {
            props: {
                posts: await res.json()
            }
        };
    }
</script>

<script>
    import Hero from '../components/Hero.svelte';
    import BlogSnippets from '../components/BlogSnippets.svelte';

    export let posts;
</script>

<Hero
    title="Steven Millard"
    subTitle="👽"
/>

<BlogSnippets {posts} title="Recent Posts" />
