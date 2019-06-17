<script>
	let name = '';
	let numberCard = '';
	let cvv = '';
	let monthCard = '';
	let yearCard = '';

	let cards = [ {numberCard:"5425585463575259", name: "Alvaro Obregon"} ];

	function send(){
		if(onlyNumber(numberCard)==true){
			cards = cards.concat({numberCard:numberCard,name:name});
		}else{
			alert("No se puede agregar el Metodo de Pago, verifique sus datos y vuelva a intentar");
		}
	}
	function onlyNumber(numberCard) {
		if (!/^([0-9])*$/.test(numberCard)){
      //alert("no es un número")
			alert("El campo "+document.getElementById("numberCard").name+" solo acepta numeros")
			return false;
		}else{
			//alert("Es un numero");
			return true;
		 }
	}
</script>

<div class="container flex">
	<div class="listCard">
		<h2><i class="fas fa-th-list"></i> Tarjetas agregadas</h2>
		<div class="list">
		{#each cards as card}
			<div class="item">
				<p>{card.numberCard}</p>
				<p>{card.name}</p>
			</div>
		{/each}
		</div>
	</div>
	<div class="dataCard">
		<h2><i class="far fa-credit-card"></i> Agregar Tarjeta</h2>
		<div class="form">
			<form action="#" class="">
				<input type="text" class="data" placeholder="Nombre Completo" bind:value={name} required>
				<input type="text" name="Numero Tarjeta" id="numberCard" class="data" placeholder="Numero Tarjeta" bind:value={numberCard} required>
				<div class="stock">
					<input type="text" class="data" placeholder="MM" bind:value={monthCard} required>
					<input type="text" class="data" placeholder="YY" bind:value={yearCard} required>
					<input type="text" class="data cvv" placeholder="CVV" bind:value={cvv} required>
				</div>
			</form>
			<div class="submit">
				<button class="boton" on:click={send}>Agregar</button>
			</div>
		</div>
		<div class="wallet">
			<div class="card" id="front">
				{#if numberCard.substr(0,1) == "4"}
					<div class="bank"><!--<img src="visa.png" alt="">-->VISA</div>
				{:else if numberCard.substr(0,1) == "5"}
					<div class="bank"><!--<img src="master.jpg" alt="">-->MASTERCARD</div>
				{:else if numberCard.substr(0,1) == "3"}
					<div class="bank"><!--<img src="amex.jpg" alt="">-->AMEX</div>
				{:else}
					<div class="bank"><!--<img src="card.jpg" alt="">-->BANCO</div>
				{/if}
				<div class="number">{numberCard || 'Número Tarjeta'}</div>
				<div class="name">{name || 'Nombre Completo'}</div>
				<div class="month">{monthCard || 'MM'} / {yearCard || 'YY'}</div>
			</div>
		</div>
	</div>
</div>


<!--
<script>
	let card = { hidde: false };

	function toggle() {
		card.hidde = !card.hidde;
	}

	let cvv = '';
</script>
<input type="text" on:focus={toggle} bind:value={cvv}>
{#if !card.hidde}
<div style=" background-color:blue; heigth:200px; width:200px;">hola</div>
{/if}

{#if card.hidde}
	<div style=" background-color:red; heigth:200px; width:200px;">hola {cvv}</div>
{/if}

<button on:focus={toggle}>Enviar</button>
*/
-->
