<script lang="ts">
	import { encode, decode } from 'bs58';
	import { Buffer } from 'buffer';

	let toEncode = '';
	let encoded = '';
	$: try {
		encoded = encode(Buffer.from(JSON.parse(toEncode)));
	} catch (err) {
		encoded = '';
	}

	let toDecode = '';
	let decoded = '';
	$: try {
		decoded = decode(toDecode).toString();
	} catch (err) {
		decoded = '';
	}
</script>

<h1>Base58 Encode</h1>
<textarea bind:value={toEncode} placeholder="[128,0,100,...]" />
<textarea readonly bind:value={encoded} placeholder="output" />

<h1>Base58 Decode</h1>
<textarea bind:value={toDecode} placeholder="Abc123..." />
<textarea readonly bind:value={decoded} placeholder="output" />

<style>
	textarea {
		width: 300px;
		height: 300px;
	}
</style>
