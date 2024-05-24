<script>
	import SketchVideos from '$lib/components/SketchVideos.svelte';
	import RandomDemo from '$lib/components/RandomDemo.svelte';
</script>

<div class="text-lg">
	<div class="flex w-full justify-center font-sans items-end bg-black">
		<div class="mx-8 max-w-3xl w-full text-white pb-12 pt-32">
			<div
				class="font-sans uppercase text-xs mb-4 tracking-widest text-gray-300 border-1 border border-solid border-gray-300 inline-block px-2 py-1 rounded-md"
			>
				supplementary videos
			</div>
			<div class="inline-block text-4xl">Diffusion On Syntax Trees For Program Synthesis</div>
			<div class="inline-block mt-8 italic text-xl">* Anonymous Authors</div>
		</div>
	</div>

	<div class="flex w-full justify-center pt-8 font-sans">
		<div class="mx-8 max-w-3xl w-full">
			<div class="w-full flex justify-center items-center flex-col">
				<div class="pb-4">
					<strong>TLDR;</strong> We teach neural models to *edit* programs, informed by the execution
					output.
				</div>
				<SketchVideos />
			</div>
		</div>
	</div>
	<div class="flex w-full justify-center pt-4 mt-16 font-sans bg-gray-100">
		<div class="mx-8 max-w-3xl w-full">
			<div class="w-full flex justify-center items-center flex-col">
				<div class="font-bold text-center text-xl mt-8">Abstract</div>
				<div class="py-4 mb-8">
					Large language models generate code one token at a time. Their autoregressive generation
					process lacks the feedback of observing the program's output. Training LLMs to suggest
					edits directly can be challenging due to the scarcity of rich edit data. To address these
					problems, we propose neural diffusion models that operate on syntax trees of any
					context-free grammar. Similar to image diffusion models, our method also inverts <q
						>noise</q
					>
					applied to syntax trees. Rather than generating code sequentially, we iteratively edit it while
					preserving syntactic validity, which makes it easy to combine this neural model with search.
					We apply our approach to inverse graphics tasks, where our model learns to convert images into
					programs that produce those images. Combined with search, our model is able to write graphics
					programs, see the execution result, and debug them to meet the required specifications. We
					additionally show how our system can write graphics programs for hand-drawn sketches.
				</div>
			</div>
		</div>
	</div>
	<div class="flex w-full justify-center pt-4 mt-16 font-sans">
		<div class="mx-8 max-w-3xl w-full">
			<h1 class="mb-8 text-3xl font-bold">What does adding <q>noise</q> mean for programs?</h1>
			<RandomDemo></RandomDemo>
			<!-- <div class="mt-4">
				What you're seeing above is our implementation of how we add random mutations to syntax
				trees.
			</div> -->
			<div class="w-full flex justify-center items-center flex-col h-32"></div>
		</div>
	</div>

	<div class="flex w-full justify-center pt-4 mt-16 font-sans">
		<div class="mx-8 max-w-3xl w-full">
			<div class="w-full flex justify-center items-center flex-col h-32"></div>
		</div>
	</div>
</div>

<style>
	.nice-shadow {
		box-shadow:
			rgba(0, 0, 0, 0.1) 0px 1px 3px 0px,
			rgba(0, 0, 0, 0.06) 0px 1px 2px 0px;
	}
</style>
