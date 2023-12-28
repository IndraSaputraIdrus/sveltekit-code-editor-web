<script lang="ts">
	import hljs from 'highlight.js';
	import js from 'highlight.js/lib/languages/javascript';
	import { onMount } from 'svelte';
	import 'highlight.js/styles/github-dark.min.css';
	import CodeHeader from './CodeHeader.svelte';

	hljs.registerLanguage('js', js);

	const highlightElement = (editor: HTMLElement) => {
		let code = editor.textContent!;
		code = hljs.highlight(code, { language: 'js' }).value;
		editor.innerHTML = code;
	};

	const initialCode = hljs.highlight(`const fo = "bar"`, { language: 'js' }).value;
	let editor: HTMLPreElement;

	onMount(async () => {
		const { CodeJar } = await import('codejar');
		CodeJar(editor, highlightElement, {
			tab: '\t'
		});
	});
</script>

<div class="rounded border border-slate-700">
  <CodeHeader />
	<!-- eslint-disable-next-line svelte/no-at-html-tags -->
	<pre bind:this={editor}>{@html initialCode}</pre>
</div>

<style lang="postcss">
	pre {
		@apply min-w-[300px] max-w-full overflow-auto overflow-auto whitespace-pre p-5 !important;
	}
</style>
