<script>
	import ExpressionPanel from './ExpressionPanel.svelte';
	import UiButton from './UIButton.svelte';
	import UndoIcon from 'virtual:icons/mi/undo';
	import RewindIcon from 'virtual:icons/mdi/rewind';
	import RandomIcon from 'virtual:icons/ion/dice-outline';
	import { loadLang } from '../lang';

	const startingExpression =
		'(- (+ (- (Circle 7 8 8) (Circle 6 8 8)) (Quad 8 8 6 6 H)) (Quad 8 8 A 1 G))';

	let currentExpression = startingExpression;

	let expressionStack = [startingExpression];

	const randomMutate = () => {
		loadLang().then((langLib) => {
			currentExpression = langLib.get_mutated(currentExpression);
			expressionStack = [...expressionStack, currentExpression];
		});
	};

	const reverseNoise = () => {
		if (expressionStack.length > 1) {
			currentExpression = expressionStack[expressionStack.length - 2];
			expressionStack = expressionStack.slice(0, expressionStack.length - 1);
		}
	};

	const resetExpression = () => {
		currentExpression = startingExpression;
		expressionStack = [startingExpression];
	};
</script>

<div class="flex flex-row">
	<UiButton on:click={resetExpression} color="black" class="mr-2">
		<div class="flex items-center">
			<UndoIcon class="inline-block" />
		</div>
	</UiButton>
	<UiButton on:click={reverseNoise} color="black" class="mr-2">
		<div class="flex items-center">
			<RewindIcon class="inline-block" />
			<span class="ml-1">Reverse Noise</span>
		</div>
	</UiButton>
	<UiButton on:click={randomMutate} color="black gradient-border" class="mr-2">
		<div class="flex items-center">
			<RandomIcon class="inline-block" />
			<span class="ml-1">Add Noise</span>
		</div>
	</UiButton>
</div>
<div class="flex flex-row my-4">
	{#each expressionStack as expression}
		<div class="mr-4 border-2 border-blue-300 border-solid rounded-md p-1">
			<ExpressionPanel size="64" {expression} />
		</div>
	{/each}
</div>

<div class="flex">
	<div class="border border-black border-solid inline-block">
		<ExpressionPanel expression={currentExpression} />
	</div>
	<div
		class="font-mono bg-gray-100 ml-4 px-4 py-4 border-2 border-solid border-gray-200 rounded-md"
	>
		{currentExpression}
	</div>
</div>
