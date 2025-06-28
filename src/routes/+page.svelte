<script lang="ts">
	let journalEntry = '';
	let quickThought = '';
	let objectives = ['First objective...']; // Sample data

	function sendQuickThought() {
		console.log('Sending quick thought:', quickThought);
		// Here you would handle the logic for the quick thought
		quickThought = '';
	}
</script>

<div class="bg-gray-100 dark:bg-gray-900 text-gray-900 dark:text-gray-100 h-screen p-4 sm:p-6 lg:p-8 font-sans">
	<div class="max-w-7xl mx-auto h-full flex flex-col">
		<!-- Top Bar -->
		<header class="mb-4">
			<div class="border border-gray-300 dark:border-gray-700 rounded-lg p-3 text-center bg-white dark:bg-gray-800 shadow-sm">
				<h1 class="text-md sm:text-lg font-semibold text-gray-600 dark:text-gray-300">Daily Journal? Check in? Ideation? Etc?</h1>
			</div>
		</header>

		<!-- Main Content -->
		<main class="flex-grow flex flex-col md:flex-row gap-4">
			<!-- Left Panel -->
			<div class="w-full md:w-2/3 flex flex-col gap-4">
				<!-- Main Journal Entry -->
				<div class="border border-gray-300 dark:border-gray-700 rounded-lg flex-grow flex flex-col p-4 bg-white dark:bg-gray-800 shadow-sm">
					<textarea
						bind:value={journalEntry}
						placeholder="What's on your mind?"
						class="w-full flex-grow bg-transparent resize-none focus:outline-none text-lg"
					></textarea>
				</div>
				<!-- Quick Thought Input -->
				<div class="flex gap-2 items-center flex-shrink-0">
					<input
						bind:value={quickThought}
						type="text"
						placeholder="Quick thought..."
						class="w-full bg-white dark:bg-gray-800 border border-gray-300 dark:border-gray-700 rounded-lg p-3 focus:outline-none focus:ring-2 focus:ring-blue-500 dark:focus:ring-blue-400 shadow-sm"
					/>
										<button 
						on:click={sendQuickThought} 
						class="bg-blue-600 hover:bg-blue-700 text-white p-3 rounded-lg transition-colors shadow-sm disabled:bg-gray-400 disabled:cursor-not-allowed"
						disabled={!quickThought.trim()}
						aria-label="Send quick thought"
					>
						<svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
							<path stroke-linecap="round" stroke-linejoin="round" d="M14 5l7 7m0 0l-7 7m7-7H3" />
						</svg>
					</button>
				</div>
			</div>

			<!-- Right Panel -->
			<div class="w-full md:w-1/3 bg-white dark:bg-gray-800 border border-gray-300 dark:border-gray-700 rounded-lg p-4 flex flex-col shadow-sm">
				<h2 class="text-xl font-bold mb-4 text-gray-800 dark:text-gray-200">Objectives/Takeaways/Goals</h2>
				<div class="flex-grow overflow-y-auto">
					<ol class="list-decimal list-inside space-y-2 text-gray-700 dark:text-gray-300">
						{#each objectives as objective}
							<li>{objective}</li>
						{/each}
					</ol>
				</div>
			</div>
		</main>
	</div>
</div>
