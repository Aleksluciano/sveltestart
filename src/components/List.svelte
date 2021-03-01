<script>
    import { createEventDispatcher } from "svelte";

    const dispatch = createEventDispatcher();
    export let irmaos = [];
</script>


<ul>
    {#each irmaos as irmao}
        <li on:click={dispatch("detalhaIrmao", irmao)}>
            <span>{irmao.nome}</span>
        </li>
    {/each}
</ul>

<style>
    ul {
        list-style-type: none;
        padding: 5px;
    }
    li {
        margin: 5px;
        cursor: pointer;
    }
    span {
        display: block;
        background-color: azure;
        min-width: 90%;
        border-radius: 10px;
        padding: 5px;
    }
</style>
