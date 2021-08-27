<script>
	import { url } from 'gravatar';
    let email;
    let size = 40;
    let loading = false;
    let src;
    let onGravatarFetch = () => {
        loading = true;
        console.log('Fetching gravatar...', loading);
        setTimeout(() => {
            src = url(email, {size});
            loading = false;
        },3000)
        console.log('Fetching completed!', loading);
    } 
</script>

<div class="flex justify-center items-center flex-col">
    <h1>fetch gravatar</h1>

    <form on:submit|preventDefault="{onGravatarFetch}">
        <input type="email" bind:value="{email}" required placeholder="Enter email to fetch gravatar" autocomplete="true">
        <input type="number" bind:value="{size}">
        <button type="submit">Fetch gravatar</button>
    </form>
</div>

<div class=" flex justify-center items-center">
    {#if loading}
        <div class="animate-spin rounded-full h-10 w-10 border-t-2 border-b-2 border-purple-500"></div>
    {:else if src}
        <img class="border border-2 ring-4 rounded-full" {src} alt="">
    {/if}
</div>