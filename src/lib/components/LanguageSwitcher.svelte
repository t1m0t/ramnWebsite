<script lang="ts">
	import { page } from '$app/state';
	import { locales, localizeHref } from '$lib/paraglide/runtime';
</script>

<div class=" float-right flex items-center gap-2">
	<div>
		{#each locales as locale}
			<a
				href={localizeHref(page.url.pathname, { locale })}
				class="hover:bg-muted rounded px-2 py-1 text-sm font-semibold transition"
				aria-current={page.url.pathname.startsWith('/' + locale) ? 'page' : undefined}
			>
				{locale.toUpperCase()}
			</a>
		{/each}
	</div>
</div>
