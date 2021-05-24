<script>
    export let type;
    export let caption; 
    export let btndisabled;
    export let bdesign;
</script>

<button type={type} class={bdesign} on:click disabled={btndisabled}>{caption}</button>

<!-- <style>
button {
    width : 120px;
    border-radius: 20px;
    background-color: #ffffff;
    color : rgba(128, 0, 0);
    font-weight: 500;
    font-size: 1.05rem;
}
</style> -->