<script lang="ts">
    import { Auth } from '@supabase/auth-ui-svelte'
	import { ThemeSupa } from '@supabase/auth-ui-shared'
    export let data;
</script>

<main>
	<h1>Register</h1>
	<Auth
			supabaseClient={data.supabase}
			view="sign_up"
			redirectTo={`${data.url}/auth/callback`}
			showLinks={false}
			appearance={{ theme: ThemeSupa, style: { input: 'color: #fff' }  }}
		/>
</main>
