<script>
 import { createEventDispatcher } from "svelte";

const dispatch = createEventDispatcher();

    export let irmao = {
        id: "",
        nome: "",
        endereco: "",
        rg: ""
    };

    const resetData = () =>{
        irmao = {
        id: "",
        nome: "",
        endereco: "",
        rg: ""
    }
    }
</script>
<button on:click={resetData}>+ NONO</button>
<div>
    <section class="details">
        <label for="nome">Nome</label>
        <input type="text" bind:value={irmao.nome} name="nome" />
    </section>
    <section class="details">
        <label for="endereco">Endereço</label>
        <input type="text" bind:value={irmao.endereco} name="endereco" />
    </section>
    <section class="details">
        <label for="endereco">RG</label>
        <input type="text" bind:value={irmao.rg} name="rg" />
    </section>
</div>
{#if irmao.nome}
<button on:click={dispatch("atualizaIrmao", irmao)}>SALVAR</button>
{/if}
{#if irmao.id}
<button on:click={dispatch("removeIrmao", irmao)}>DELETAR</button>
{/if}
<style>
    .details {
        display: inline-block;
        margin: 15px;
    }

</style>
