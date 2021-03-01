<script>
    import Nav from "$components/Nav.svelte";
</script>

<main>
    <div class="center">
        <Nav />
    </div>
    <div class="margin">
        <slot />
    </div>
</main>

<style>
    .center {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .margin {
        margin: 0 5em;
    }

    :global(input,label,span) {
        padding: 6px;
        font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
            "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
    }

</style>
