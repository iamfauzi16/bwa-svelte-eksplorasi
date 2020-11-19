<script>
    let description = '';
    $: characters = description.length;
    $: words = description.split(' ').length;

    $: if(description.length > 10 ){
        console.log('-----');
        console.log(`Description: ${description}`);
    }
</script>

<style>
    div {
        margin-top: 1em ;
        margin-bottom: 1em;
    }
</style>

<div>
    <p>{description}</p>
    <textarea bind:value={description} rows="7" />
    <p>Characters count: {characters}</p>
    <p>Words Count: {words}</p>
</div>