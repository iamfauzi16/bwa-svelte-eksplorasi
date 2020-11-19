<script>
let current = 'button1';
export let currentEmoji;
</script>


<!-- Scope -->
<style>
    div {
        font-size: 3em;
        margin-bottom: 10px;
    }

    button {
        color: orange;
    }

    .active {
        background-color : red;
        color: #fff;
    }
    
</style>

<div>{currentEmoji}</div>
<button
    class:active={current === 'button1'}
    on:click={() => (current = 'button1')}>
    Button 1

</button>
<button
    class:active={current === 'button2'}
    on:click={() => (current = 'button2')}>
    Button 2
</button>

<button
    class:active={current === 'button3'}
    on:click={() => (current = 'button3')}>
    Button 3
</button>