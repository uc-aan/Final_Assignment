<script>
    import { qReffrence } from '../store/question-store.js';
    import { reviewStatus } from '../store/review-store.js';
    import App from '../App.svelte';
    import ExitBox from './ExitBox.svelte';
    import { showSection } from '../store/list-store.js';

    let startTest = true;
    let restartApp = false;
    export let attempted=0;
    let exitTest = false;

    function handleExitBox() {
        exitTest = true;  
    }

    function restartTest() {
        reviewStatus.update((value) => {
            return false;
        });
        startTest = !startTest;
        restartApp = !restartApp;
        document.location.reload();
    }

    function updateReview() {
        reviewStatus.update((value) => {
            return true;
        });
        qReffrence.update((value) => {
            return 0 ;
        });
        startTest = false;
    }

 </script>

{#if exitTest}
<ExitBox />
{/if}
 
 {#if startTest}
 <div class="backdrop">
     <div class="main">
         <h1>SCORE</h1>
         <hr>
         <h2>Attempted    : {attempted}</h2>
         <h2>Un-Attempted : {10 - attempted}</h2>
         <div class="btn_row">  
            <button type="button" class="btn btn-outline-danger button1" on:click={restartTest}>RESTART</button>
            <button type="button" class="btn btn-outline-info button2" on:click={updateReview}>REVIEW</button>
            <button type="button" class="btn btn-outline-danger button3" on:click={handleExitBox}>EXIT</button>
        </div>     
     </div>
 </div>
 {:else}
    <App />
 {/if}


<style>
.backdrop {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 9999;
    background-color: rgba(0, 0, 0, 0.9);
}
.main{
    position: fixed;
    top: calc(50% - 150px);
    left: calc(50% - 300px);
    height: 250px;
    width: 600px;
    background-color: #ffffff;
    z-index: 9999;
}
.main h1 {
    font-weight: 400;
    font-size: 1.85rem;
    text-align: center;
}
.main h2 {
    font-weight: 400;
    font-size: 1.85rem;
    margin: 0;
    padding: 0;
    text-transform: uppercase;
    width: 100;
    display: flex;
    justify-content: center;
}
hr {
    border: 1px double red;
}
.btn_row {
    width: 100%;
    border-radius: 15px;
    margin-top: 2rem;
    padding: 0.5rem;
    display: flex;
    justify-content: space-between;
}
.button1 {
    width: 10rem;
    font-weight: bolder;
    font-size: 20px;
    margin-left: 5rem;
}
.button2 {
    width: 10rem;
    font-weight: bolder;
    font-size: 20px;
    margin-right: 5rem;
}
</style>