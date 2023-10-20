<script>
	let bill = 0;
	let tip = 0;
	let numPeople = 1;
	$: tipAmountPerPerson = (bill * tip) / 100 / numPeople;
	$: totalPerPerson = bill / numPeople + tipAmountPerPerson;

	function handleReset() {
		bill = 0;
		tip = 0;
		numPeople = 1;
	}
</script>

<header class="title">
	<h1>SPLI <br />TTER</h1>
</header>
<main class="calc-container">
	<article class="calc">
		<div>
			<header class="input-container">
				<h2>Bill</h2>
				<input type="number" class="dollar-icon" bind:value={bill} />
			</header>
			<section class="tip-selection">
				<h2>Select Tip %</h2>
				<ul class="tips">
					<li>
						<button
							on:click={() => {
								tip = 5;
							}}>5%</button
						>
					</li>
					<li>
						<button
							on:click={() => {
								tip = 10;
							}}>10%</button
						>
					</li>
					<li>
						<button
							on:click={() => {
								tip = 15;
							}}>15%</button
						>
					</li>
					<li>
						<button
							on:click={() => {
								tip = 25;
							}}>25%</button
						>
					</li>
					<li>
						<button
							on:click={() => {
								tip = 50;
							}}>50%</button
						>
					</li>
					<input
						type="number"
						placeholder="Custom"
						step="1"
						min="0"
						max="100"
						bind:value={tip}
						class="custom-tip"
					/>
				</ul>
			</section>
			<section class="num-of-people input-container">
				<h2>Number of People</h2>
				<input type="number" class="person-icon" bind:value={numPeople} min="1" step="1" />
			</section>
		</div>
		<section class="total-calculator">
			<div class="amount-summary">
				<div class="amount-display">
					<div>
						<h2>Tip Amount</h2>
						<p>/ person</p>
					</div>
					<p>${tipAmountPerPerson}</p>
				</div>
				<div class="amount-display">
					<div>
						<h2>Total</h2>
						<p>/ person</p>
					</div>
					<p>${totalPerPerson}</p>
				</div>
			</div>
			<button on:click={handleReset}>RESET</button>
		</section>
	</article>
</main>

<style>
	:root {
		--calc-background: hsl(0, 0%, 100%);

		--strong-cyan: hsl(172, 67%, 45%);
		--very-dark-cyan: hsl(183, 100%, 15%);
		--dark-grayish-cyan: hsl(186, 14%, 43%);
		--grayish-cyan: hsl(184, 14%, 56%);
		--light-grayish-cyan: hsl(185, 41%, 84%);
		--very-dark-cyan: hsl(183, 100%, 15%);
		--very-light-greyish-cyan: hsl(189, 41%, 97%);

		--calc-padding: 2rem;
	}

	.title {
		height: 15%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.calc-container {
		width: 100%;
		height: 75%;
	}

	.calc {
		width: calc(100% - --calc-padding - --calc-padding);
		border-radius: 1rem 1rem 0 0;
		padding: var(--calc-padding);
		background-color: var(--calc-background);
	}
	article {
		display: flex;
		flex-direction: column;
		gap: 1rem;
	}

	header {
		display: flex;
		flex-direction: column;
		gap: 0.5rem;
	}

	header > h1 {
		font-size: 24px;
		letter-spacing: 0.5rem;
		color: hsl(183, 100%, 15%);
	}

	.input-container > h2 {
		color: var(--dark-grayish-cyan);
	}

	.input-container > input {
		background-color: var(--very-light-greyish-cyan);
		border-radius: 0.75rem;
		padding-top: 1.25rem;
		padding-bottom: 1.25rem;
		border: none;
		color: var(--very-dark-cyan);
		width: 100%;
		height: 100%;
		font-size: 24px;
		text-align: right;
	}
	.dollar-icon {
		background: url('/assets/images/icon-dollar.svg');
		background-size: 1rem;
		background-repeat: no-repeat;
		background-position: 1rem 50%;
	}

	.tip-selection {
		display: flex;
		flex-direction: column;
		gap: 1rem;
	}

	.tip-selection > h2 {
		color: var(--dark-grayish-cyan);
	}

	.tips {
		display: grid;
		grid-template-columns: 1fr 1fr;
		grid-template-rows: repeat(4, 1fr);
		gap: 1rem;
		height: 12rem;
	}

	.tips > li,
	.tips > input {
		text-align: center;
		color: var(--very-light-greyish-cyan);
		border-radius: 0.5rem;
		font-size: 24px;
		font-weight: 600;
		padding-top: 0.75rem;
		padding-bottom: 0.75rem;
		padding-left: 1rem;
		padding-right: 1rem;
		background-color: var(--very-dark-cyan);
		cursor: pointer;
	}
	.tips > li:hover {
		color: var(--very-dark-cyan);
		background-color: var(--light-grayish-cyan);
	}

	input.custom-tip {
		color: var(--dark-grayish-cyan);
		background-color: var(--very-light-greyish-cyan);
		border: none;
	}

	.num-of-people {
		display: flex;
		flex-direction: column;
		gap: 1rem;
	}

	.num-of-people > h2 {
		color: var(--dark-grayish-cyan);
	}

	.num-of-people > input {
		background-color: var(--very-light-greyish-cyan);
		border-radius: 0.75rem;
		padding-top: 1.25rem;
		padding-bottom: 1.25rem;
		border: none;
		color: var(--very-dark-cyan);
		width: 100%;
		height: 100%;
		font-size: 24px;
		text-align: right;
	}

	input[type='number']:focus {
		outline-color: var(--strong-cyan);
	}

	.person-icon {
		background: url('/assets/images/icon-person.svg');
		background-size: 1rem;
		background-repeat: no-repeat;
		background-position: 1rem 50%;
	}

	.total-calculator {
		display: flex;
		flex-direction: column;
		background-color: var(--very-dark-cyan);
		border-radius: 1rem;
		padding: 2rem;
		gap: 2rem;
	}

	.amount-summary {
		display: flex;
		flex-direction: column;
		gap: 2rem;
	}

	.amount-summary > div {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
	}

	.amount-display > div > h2 {
		color: var(--very-light-greyish-cyan);
		font-weight: 500;
	}
	.amount-display > div > p {
		color: var(--dark-grayish-cyan);
		font-weight: 500;
	}
	.amount-display > p {
		font-size: 1.5rem;
		color: var(--strong-cyan);
	}
	.total-calculator > button {
		background-color: var(--strong-cyan);
		color: var(--very-dark-cyan);
		font-size: 1.25rem;
		font-weight: 700;
		border-radius: 0.5rem;
		padding-top: 0.75rem;
		padding-bottom: 0.75rem;
	}

	.total-calculator > button:hover {
		background-color: var(--light-grayish-cyan);
	}

	@media screen and (min-width: 480px) {
		.calc-container {
			height: fit-content;
			display: flex;
			flex-direction: row;
			justify-content: center;
			align-items: center;
		}
		.calc {
			border-radius: 1rem;
			width: 40%;
			display: flex;
			flex-direction: row;
			height: fit-content;
			gap: 2rem;
		}
		.calc > div {
			display: flex;
			flex-direction: column;
			gap: 2rem;
			width: 60%;
		}
		.calc > section {
			width: 40%;
		}

		.tips {
			display: grid;
			grid-template-columns: repeat(3, 1fr);
			grid-template-rows: 1fr 1fr;
			gap: 1rem;
			height: 8rem;
		}
		.title {
			height: 25%;
		}

		.total-calculator {
			justify-content: space-between;
		}
		.amount-display > p {
			font-size: 2.5rem;
		}
	}
</style>
