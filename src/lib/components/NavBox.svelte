<script>
    import Icon from "./Icon.svelte";

    export let icon = '';
    export let title = '';
    export let subTitle = '';
</script>

<div class="p-2 w-1/5 transition hover:scale-110 hover:bg-surface-400 bg-surface-500 border border-primary-400 shadow-xl rounded-md grid grid-cols-1" on:click on:keyup>
    <Icon />
    <span class="text-base text-primary-700 underline">{title}</span>
    <span class="text-xs text-primary-500 my-2">{subTitle}</span>
</div>