<script lang="ts">
	import { m } from '$lib/paraglide/messages.js';
	import { COMPANY_NAME } from '$lib/config';
	import LanguageSwitcher from '$lib/components/LanguageSwitcher.svelte';
	import { onMount } from 'svelte';
	import { page } from '$app/state';

	let showUp = $state(false);

	type ServiceText = {
		title: string;
		description: string;
	};

	type PlanAndPriceText = {
		title: string;
		description: string;
		price: string;
		features: string[];
	};

	let servicesText: ServiceText[] = $state([]);

	let plansAndPricesText: PlanAndPriceText[] = $state([]);
	let headTitle: string = $state(m['head.title']());
	let headDescription: string = $state(m['head.description']());
	let menuTranslations: string[] = $state([
		m['menu.services'](),
		m['menu.plans'](),
		m['menu.about'](),
		m['menu.contact']()
	]);
	let getStartedTranslation: string = $state(m['get_started']());
	let sectionTitleTranslation: {
		services: string;
		plans: string;
		about: string;
		contact: string;
	} = $state({
		services: m['sections.services'](),
		plans: m['sections.plans'](),
		about: m['sections.about'](),
		contact: m['sections.contact']()
	});
	let aboutUsTranslation: { title: string; description: string } = $state({
		title: m['about_us.title'](),
		description: m['about_us.description']()
	});
	let contactUsTranslation: {
		title: string;
		description: string;
		form: {
			name: string;
			name_placeholder: string;
			email: string;
			email_placeholder: string;
			message: string;
			message_placeholder: string;
			submit: string;
		};
	} = $state({
		title: m['contact_us.title'](),
		description: m['contact_us.description'](),
		form: {
			name: m['contact_us.form.name'](),
			name_placeholder: m['contact_us.form.name_placeholder'](),
			email: m['contact_us.form.email'](),
			email_placeholder: m['contact_us.form.email_placeholder'](),
			message: m['contact_us.form.message'](),
			message_placeholder: m['contact_us.form.message_placeholder'](),
			submit: m['contact_us.form.submit']()
		}
	});

	onMount(() => {
		setTranslations();
	});

	$effect(() => {
		if (page.url.pathname) {
			setTranslations();
		}
	});

	function setTranslations() {
		headTitle = m['head.title']();
		headDescription = m['head.description']();
		getStartedTranslation = m['get_started']();
		menuTranslations = [
			m['menu.services'](),
			m['menu.plans'](),
			m['menu.about'](),
			m['menu.contact']()
		];
		sectionTitleTranslation = {
			services: m['sections.services'](),
			plans: m['sections.plans'](),
			about: m['sections.about'](),
			contact: m['sections.contact']()
		};
		aboutUsTranslation = {
			title: m['about_us.title'](),
			description: m['about_us.description']()
		};
		contactUsTranslation = {
			title: m['contact_us.title'](),
			description: m['contact_us.description'](),
			form: {
				name: m['contact_us.form.name'](),
				name_placeholder: m['contact_us.form.name_placeholder'](),
				email: m['contact_us.form.email'](),
				email_placeholder: m['contact_us.form.email_placeholder'](),
				message: m['contact_us.form.message'](),
				message_placeholder: m['contact_us.form.message_placeholder'](),
				submit: m['contact_us.form.submit']()
			}
		};
		servicesText = [
			{
				title: m['services.home_care.title'](),
				description: m['services.home_care.description']()
			},
			{
				title: m['services.return_preparation_services.title'](),
				description: m['services.return_preparation_services.description']()
			},
			// {
			// 	title: 'Car Care',
			// 	description:
			// 		'Making sure your car is clean, functioning and safe with regular check-ups. Maintenance provided!'
			// },
			{
				title: m['services.property_security.title'](),
				description: m['services.property_security.description']()
			},
			{
				title: m['services.emergency_services.title'](),
				description: m['services.emergency_services.description']()
			}
		];

		plansAndPricesText = [
			{
				title: m['plans.essential.title'](),
				description: m['plans.essential.description'](),
				price: m['plans.essential.price'](),
				features: [
					m['plans.essential.features.0'](),
					m['plans.essential.features.1'](),
					m['plans.essential.features.2'](),
					m['plans.essential.features.3'](),
					m['plans.essential.features.4'](),
					m['plans.essential.features.5'](),
					m['plans.essential.features.6']()
				]
			},
			{
				title: m['plans.comfort.title'](),
				description: m['plans.comfort.description'](),
				price: m['plans.comfort.price'](),
				features: [
					m['plans.comfort.features.0'](),
					m['plans.comfort.features.1'](),
					m['plans.comfort.features.2'](),
					m['plans.comfort.features.3'](),
					m['plans.comfort.features.4'](),
					m['plans.comfort.features.5'](),
					m['plans.comfort.features.6'](),
					m['plans.comfort.features.7'](),
					m['plans.comfort.features.8'](),
					m['plans.comfort.features.9']()
				]
			},
			{
				title: m['plans.executive.title'](),
				description: m['plans.executive.description'](),
				price: m['plans.executive.price'](),
				features: [
					m['plans.executive.features.0'](),
					m['plans.executive.features.1'](),
					m['plans.executive.features.2'](),
					m['plans.executive.features.3'](),
					m['plans.executive.features.4'](),
					m['plans.executive.features.5'](),
					m['plans.executive.features.6'](),
					m['plans.executive.features.7'](),
					m['plans.executive.features.8'](),
					m['plans.executive.features.9'](),
					m['plans.executive.features.10'](),
					m['plans.executive.features.11'](),
					m['plans.executive.features.12']()
				]
			},
			{
				title: m['plans.signature.title'](),
				description: m['plans.signature.description'](),
				price: m['plans.signature.price'](),
				features: [
					m['plans.signature.features.0'](),
					m['plans.signature.features.1'](),
					m['plans.signature.features.2'](),
					m['plans.signature.features.3'](),
					m['plans.signature.features.4'](),
					m['plans.signature.features.5'](),
					m['plans.signature.features.6'](),
					m['plans.signature.features.7'](),
					m['plans.signature.features.8'](),
					m['plans.signature.features.9'](),
					m['plans.signature.features.10'](),
					m['plans.signature.features.11'](),
					m['plans.signature.features.12'](),
					m['plans.signature.features.13'](),
					m['plans.signature.features.14'](),
					m['plans.signature.features.15']()
				]
			},
			{
				title: m['plans.bespoke.title'](),
				description: m['plans.bespoke.description'](),
				price: m['plans.bespoke.price'](),
				features: [
					m['plans.bespoke.features.0'](),
					m['plans.bespoke.features.1'](),
					m['plans.bespoke.features.2'](),
					m['plans.bespoke.features.3'](),
					m['plans.bespoke.features.4'](),
					m['plans.bespoke.features.5'](),
					m['plans.bespoke.features.6'](),
					m['plans.bespoke.features.7'](),
					m['plans.bespoke.features.8'](),
					m['plans.bespoke.features.9'](),
					m['plans.bespoke.features.10'](),
					m['plans.bespoke.features.11'](),
					m['plans.bespoke.features.12'](),
					m['plans.bespoke.features.13'](),
					m['plans.bespoke.features.14'](),
					m['plans.bespoke.features.15'](),
					m['plans.bespoke.features.16']()
				]
			}
		];
	}

	// Show button after scrolling 200px
	if (typeof window !== 'undefined') {
		window.addEventListener('scroll', () => {
			showUp = window.scrollY > 200;
		});
	}

	function scrollToTop() {
		window.scrollTo({ top: 0, behavior: 'smooth' });
	}
</script>

{#if showUp}
	<button
		onclick={scrollToTop}
		class="bg-primary hover:bg-primary/90 fixed right-6 bottom-6 z-50 rounded-full p-3 text-white shadow-lg transition"
		aria-label="Scroll to top"
	>
		<svg
			xmlns="http://www.w3.org/2000/svg"
			class="h-6 w-6"
			fill="none"
			viewBox="0 0 24 24"
			stroke="currentColor"
		>
			<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 15l7-7 7 7" />
		</svg>
	</button>
{/if}

{#snippet services(data: ServiceText)}
	<div
		class="bg-card group rounded-lg p-6 shadow transition hover:cursor-pointer hover:bg-emerald-100 hover:shadow-lg"
	>
		<h4 class="mb-2 text-xl font-semibold group-hover:underline">{data.title}</h4>
		<p class="text-muted-foreground">
			{data.description}
		</p>
	</div>
{/snippet}

{#snippet plans(data: PlanAndPriceText)}
	<div class="bg-card rounded-lg p-6 shadow">
		<h4 class="mb-2 text-xl font-semibold lg:h-[2rem]">{data.title}</h4>
		<p class="text-muted-foreground mb-4 lg:h-[6rem]">
			{data.description}
		</p>
		<p class="mb-4 text-2xl font-bold lg:h-[6rem]">{data.price}</p>
		<ul class="text-muted-foreground list-disc pl-5">
			{#each data.features as feature}
				<li>{feature}</li>
			{/each}
		</ul>
		<a
			href="#contact"
			class="bg-primary hover:bg-primary/90 mt-4 inline-block rounded px-6 py-3 font-semibold text-white shadow transition"
		>
			Choose Plan
		</a>
	</div>
{/snippet}

<!-- ShadCN base styles (make sure shadcn/tailwind is set up in your project) -->
<div class="bg-background text-foreground min-h-screen font-sans">
	<!-- Header -->
	<header class="bg-card border-b shadow-sm">
		<div class="container mx-auto flex items-center justify-between px-4 py-6">
			<div class="flex items-center gap-3">
				<h1 class="text-2xl font-bold tracking-tight">{COMPANY_NAME}</h1>
			</div>
			<nav>
				<div class="flex flex-col place-content-end">
					<div>
						<LanguageSwitcher />
					</div>
					<div class="flex flex-col gap-1 space-x-6 md:flex-row">
						<a href="#services" class="hover:underline">{menuTranslations[0]}</a>
						<a href="#plans" class="hover:underline">{menuTranslations[1]}</a>
						<a href="#about" class="hover:underline">{menuTranslations[2]}</a>
						<a href="#contact" class="hover:underline">{menuTranslations[3]}</a>
					</div>
				</div>
			</nav>
		</div>
	</header>

	<!-- Hero Section -->
	<section
		class="container mx-auto flex flex-col items-center justify-center px-4 py-20 text-center"
	>
		<div class="mb-8 flex flex-col items-center gap-3 sm:flex-row">
			<img src="/logo.jpg" alt="SuppaVisor Logo" class="h-40 w-40 rounded" />
			<div>
				<h2 class="mb-4 text-4xl font-extrabold">
					{headTitle}
				</h2>
				<p class="text-muted-foreground mb-8 text-lg">
					{headDescription}
				</p>
			</div>
		</div>

		<a
			href="#contact"
			class="bg-primary hover:bg-primary/90 inline-block rounded px-6 py-3 font-semibold text-white shadow transition"
		>
			{getStartedTranslation}
		</a>
	</section>

	<!-- Services Section -->
	<section id="services" class="container mx-auto px-4 py-16">
		<h3 class="mb-8 text-center text-3xl font-bold">
			{sectionTitleTranslation.services}
		</h3>
		<div class="grid grid-cols-1 gap-8 md:grid-cols-2">
			{#each servicesText as service}
				{@render services(service)}
			{/each}
		</div>
	</section>

	<!-- Pricing Plans Section -->
	<section id="plans" class="container mx-auto px-4 py-16">
		<h3 class="mb-8 text-center text-3xl font-bold">{sectionTitleTranslation.plans}</h3>
		<div class="grid grid-cols-1 gap-8 md:grid-cols-5">
			{#each plansAndPricesText as plan}
				{@render plans(plan)}
			{/each}
		</div>
	</section>

	<!-- About Section -->
	<section id="about" class="container mx-auto px-4 py-16">
		<h3 class="mb-6 text-center text-3xl font-bold">{aboutUsTranslation.title}</h3>
		<p class="text-muted-foreground mx-auto max-w-2xl text-center">
			{aboutUsTranslation.description}
		</p>
	</section>

	<!-- Contact Section -->
	<section id="contact" class="container mx-auto px-4 py-16">
		<h3 class="mb-6 text-center text-3xl font-bold">{contactUsTranslation.title}</h3>
		<form class="bg-card mx-auto max-w-xl space-y-6 rounded-lg p-8 shadow">
			<p class="text-muted-foreground mx-auto max-w-2xl text-center">
				{contactUsTranslation.description}
			</p>
			<div>
				<label class="mb-2 block font-medium" for="name">{contactUsTranslation.form.name}</label>
				<input
					id="name"
					type="text"
					class="input input-bordered w-full"
					placeholder={contactUsTranslation.form.name_placeholder}
					required
				/>
			</div>
			<div>
				<label class="mb-2 block font-medium" for="email">{contactUsTranslation.form.email}</label>
				<input
					id="email"
					type="email"
					class="input input-bordered w-full"
					placeholder={contactUsTranslation.form.email_placeholder}
					required
				/>
			</div>
			<div>
				<label class="mb-2 block font-medium" for="message"
					>{contactUsTranslation.form.message}</label
				>
				<textarea
					id="message"
					class="input input-bordered min-h-[100px] w-full"
					placeholder={contactUsTranslation.form.message_placeholder}
					required
				></textarea>
			</div>
			<button
				type="submit"
				class="bg-primary hover:bg-primary/90 w-full rounded px-6 py-3 font-semibold text-white shadow transition"
			>
				{contactUsTranslation.form.submit}
			</button>
		</form>
	</section>

	<!-- Footer -->
	<footer class="bg-card mt-16 border-t py-6">
		<div class="text-muted-foreground container mx-auto text-center text-sm">
			&copy; {new Date().getFullYear()}
			{COMPANY_NAME}. {m.all_rights_reserved()}
		</div>
	</footer>
</div>
