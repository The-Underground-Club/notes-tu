<script>
	import { marked } from 'marked';
	let markdown;
</script>
To learn more, head <a href="https://www.markdownguide.org/cheat-sheet/" target="_blank">here</a> to start writing in Markdown!
<div class="grow-wrap">
	<textarea bind:value={markdown} placeholder="Start typing..." class="source" onInput="this.parentNode.dataset.replicatedValue=this.value"></textarea>
</div>

{#if markdown != null}
<hr>
<div class="output">{@html marked(markdown)}</div>
{/if}

<style>
.grow-wrap {
	display: grid;
}
.grow-wrap::after {
	content: attr(data-replicated-value) " ";
	white-space: pre-wrap;
	visibility: hidden;
}
.grow-wrap > textarea {
	resize: none;
	overflow: hidden;
}
.output,
.grow-wrap > textarea,
.grow-wrap::after {
	padding: 0.5rem;
	font: inherit;
	grid-area: 1 / 1 / 2 / 2;
}
.output {
	display: block;
}
</style>