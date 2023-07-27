<!-- src/routes/+layout.svelte -->
<script lang="ts">
	import '../styles.css';
    import '../app.css'; 
    import Header from './Header.svelte';
    import Footer from './Footer.svelte';
    
	import { invalidate } from '$app/navigation'
	import { onMount } from 'svelte'
	import type { PageData } from './$types'

	export let data: PageData;

	let { supabase, session } = data
	$: ({ supabase, session } = data)

	onMount(() => {
		const { data } = supabase.auth.onAuthStateChange((event, _session) => {
			if (_session?.expires_at !== session?.expires_at) {
				invalidate('supabase:auth')
			}
		})

		return () => data.subscription.unsubscribe()
	})
</script>

<svelte:head>
	<title>User Management</title>
</svelte:head>

  
<Header data={data}/>
<div class="container" style="padding: 50px 0 20px 0; height:90vh">
   
	<slot />
   
</div>
<Footer/>