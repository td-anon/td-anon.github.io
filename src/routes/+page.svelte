<script>
	let heroVideos = [
		{ video: '/videos/sketch4.mp4', title: 'Sketch 4', thumbnail: '/videos/sketch4.png' },
		{ video: '/videos/sketch1.mp4', title: 'Sketch 1', thumbnail: '/videos/sketch1.png' },
		{ video: '/videos/sketch5.mp4', title: 'Sketch 5', thumbnail: '/videos/sketch5.png' },
		{ video: '/videos/sketch3.mp4', title: 'Sketch 3', thumbnail: '/videos/sketch3.png' },
		{ video: '/videos/sketch2.mp4', title: 'Sketch 2', thumbnail: '/videos/sketch2.png' }
	];

	let currentVideo = heroVideos[0];
</script>

<div class="flex w-full justify-center font-serif items-end bg-black">
	<div class="mx-8 max-w-4xl w-full text-white pb-12 pt-32">
		<div
			class="font-sans uppercase text-xs mb-4 tracking-widest text-gray-300 border-1 border border-solid border-gray-300 inline-block px-2 py-1 rounded-md"
		>
			supplementary videos
		</div>
		<div class="inline-block text-4xl">Diffusion On Syntax Trees For Program Synthesis</div>
		<div class="inline-block mt-8 italic text-xl">* Anonymous Authors</div>
	</div>
</div>

<div class="flex w-full justify-center pt-8 font-serif">
	<div class="mx-8 max-w-4xl w-full">
		<div class="w-full flex justify-center items-center flex-col">
			<div class="pb-4">
				<strong>TLDR;</strong> We teach neural models to *edit* programs. <br /> After each edit, the
				model can look at the output.
			</div>
			<div class="border-2 border-gray-300 border-solid inline-block p-8 rounded-md">
				<video src={currentVideo.video} autoplay loop muted class="max-w-xl w-full"></video>
			</div>
			<div class="mt-4 italic">(Select A Sketch Below)</div>
			<div class="md:flex md:flex-row md:justify-center md:items-center mt-2">
				{#each heroVideos as video}
					<button
						class="transition border-2 border-solid w-24 h-24 p-2 rounded-md m-2 cursor-pointer"
						class:border-gray-300={currentVideo !== video}
						class:hover:border-gray-500={currentVideo !== video}
						class:border-blue-500={currentVideo === video}
						class:hover:border-blue-500={currentVideo === video}
						class:nice-shadow={currentVideo === video}
						on:click={() => (currentVideo = video)}
					>
						<img src={video.thumbnail} alt={video.thumbnail} class="w-full h-full" />
					</button>
				{/each}
			</div>
		</div>
	</div>
</div>
<div class="flex w-full justify-center pt-4 mt-16 font-serif bg-gray-100">
	<div class="mx-8 max-w-4xl w-full">
		<div class="w-full flex justify-center items-center flex-col">
			<div class="font-bold text-center text-xl mt-8">Abstract</div>
			<div class="py-4 mb-8">
				Large language models typically generate code autoregressively, one token at a time. This
				can make it difficult to enforce syntactic constraints or to use the language model as a
				proposal distribution for search. To address these problems, we propose neural diffusion
				models that operate on syntax trees of any context-free grammar. Similar to image diffusion
				models, they invert <q>noise</q> added to these syntax trees. Rather than generating code sequentially,
				they iteratively edit it while preserving syntactic validity, which makes it easy to combine
				this neural model with search. We apply our approach to inverse graphics tasks, where our model
				learns to convert images into programs that produce those images. Combined with search, our model
				is thus able to write graphics programs, see the execution result, and debug them to meet the
				required specification. We additionally show how our system can write graphics programs for hand-drawn
				sketches.
			</div>
		</div>
	</div>
</div>
<div class="flex w-full justify-center pt-4 mt-16 font-serif">
	<div class="mx-8 max-w-4xl w-full">
		<div class="w-full flex justify-center items-center flex-col h-32"></div>
	</div>
</div>

<style>
	.nice-shadow {
		box-shadow:
			rgba(0, 0, 0, 0.1) 0px 1px 3px 0px,
			rgba(0, 0, 0, 0.06) 0px 1px 2px 0px;
	}
</style>
