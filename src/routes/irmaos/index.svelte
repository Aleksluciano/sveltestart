<script>
    import List from "$components/List.svelte";
    import Detail from "$components/Detail.svelte";
    import fakeIrmaos from "$components/fakeData/fakeIrmaos.js";
  

    let irmaos = fakeIrmaos;
    let irmao = { ...irmaos[0] };

    const handleDetalhaIrmao = (e) => {
        console.log(e.detail);
        irmao = { ...e.detail };
    };
    const handleAtualizaIrmao = (e) => {
        if (e.detail.id && e.detail.nome) {
            let indexIrmao = irmaos.findIndex((a) => a.id == e.detail.id);
            if (indexIrmao >= 0) irmaos.splice(indexIrmao, 1);
            irmaos = [e.detail, ...irmaos];
        } else if (e.detail.nome) {
            irmao = e.detail;
            irmao.id = Math.random();
            irmaos = [...e.detail, ...irmaos];
        }
    };

    const handleRemoveIrmao = (e) => {
        let indexIrmao = irmaos.findIndex((a) => a.id == e.detail.id);
        if (indexIrmao >= 0) irmaos.splice(indexIrmao, 1);
        irmaos = [...irmaos];
    };
</script>

<div class="site">
    <nav class="site-nav">
        <List {irmaos} on:detalhaIrmao={handleDetalhaIrmao} />
    </nav>
    <main class="site-content">
        <div class="details">
            <Detail
                {irmao}
                on:atualizaIrmao={handleAtualizaIrmao}
                on:removeIrmao={handleRemoveIrmao}
            />
        </div>
    </main>
</div>

<style>
    .site {
        display: flex;
        min-height: 80vh;
        border: black 2px solid;
    }

    .site-nav {
        background: #95dcee;
        width: 20em;
        display: flex;
        flex-direction: column;
        justify-content: start;
    }

    .site-content {
        background: rgb(238, 238, 238);
        flex: 1;
        justify-content: space-around;
    }
</style>
