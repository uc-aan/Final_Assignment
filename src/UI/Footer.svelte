<script>
    import { qReffrence } from '../store/question-store.js'; 
    import { showSection } from '../store/list-store.js';
    import Timer from '../component/Timer.svelte';
    import ConfirmBox from '../component/ConfirmBox.svelte';
    import { reviewStatus } from '../store/review-store';
    import { onDestroy } from 'svelte';
    import Score from '../component/Score.svelte';

    let showTimer = true;
    let showModal = false;
    let startValue = 0;
    let disablebtn;
    let data = 0;

    function Previous() {
        qReffrence.update((value) => {
            data = value-1;
            return value-1 ;
        });
        startValue-=1;
    }

    function Next() {
        qReffrence.update((value) => {
            data = value+1;
            return value+1 ;
        });
       startValue+=1;
    }

    function handleShowSection() {
        showSection.update((value) => {
            return true;
        });
    }

    function endTest() {
        showModal = !showModal;
        startValue = 0;
        qReffrence.update((value) => {
            return 0;
        });
    }

    $: if(data < 1) {
        disablebtn = true;
    }
    else {
        disablebtn = false;
    }

    const unsubscribetimer= reviewStatus.subscribe((data) => {
        showTimer = data;
    });
    
    onDestroy(unsubscribetimer);
</script>

{#if showModal}
    <Score />
{/if}

<footer>
    <div class="Footer">

        {#if !showTimer} 
        <Timer />
        {/if}
        <button type="button" class="btn btn-outline-info" on:click="{handleShowSection}">List</button>
        <button type="button" class="btn btn-outline-primary" on:click="{Previous}" disabled={disablebtn} >Previous</button>
        <p>{data+1} of 10</p>
        <button type="button" class="btn btn-outline-success" on:click="{Next}" id="btnN" >Next</button>
        <button type="button" class="btn btn-outline-danger" on:click="{endTest}">End Test</button>
        
    </div>
</footer>

<style>
    
.Footer {
        display: flex;
        justify-content: space-between;
        padding: 0.5em;
    }

    footer {
        position: fixed;
        top: 40.5rem;
        background-color: black ;
        display: flex;
        justify-content: center;
        align-items: center;
        width: 98%;
        left: 1rem;
        box-shadow: -1px -3px 4px -1px rgba(0,0,0,0.63);
    }
    
    button {
        font-weight: bolder;
        width: 150px;
        border-radius: 5px;
        margin-left: 1rem;
    }
    p {
        margin-left: 1rem;
        color: white;
    }
</style>