<!-- src/routes/+page.svelte -->
<script lang="ts">
	import { Auth } from '@supabase/auth-ui-svelte'
	import { ThemeSupa } from '@supabase/auth-ui-shared'
	import { ThemeMinimal } from '@supabase/auth-ui-shared'
	import type { PageData } from './$types'

	export let data: PageData
    console.log(data)
</script>

<svelte:head>
	<title>User Management</title>
</svelte:head>
<main>
    <div class="row flex-center flex">
   
        <div class="col-6 form-widget">
            <Auth
                supabaseClient={data.supabase}
                view="sign_in"
                redirectTo={`${data.url}/auth/callback`}
                showLinks={false}
                appearance={{ theme: ThemeSupa, style: { input: 'color: #fff' } }}
            />
        </div>
       
    </div>
</main>

