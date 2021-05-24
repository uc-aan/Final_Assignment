<script>
    import Score from './Score.svelte'; 

    let showModal = true;
    let showScore = false;

    function closeModal() {
       showModal = false;
    }
    function openScore() {
        showModal = !showModal;
        showScore = !showScore;
    }
</script>


{#if showModal}
<div class="backdrop">
    <div class="modal">
        <h1>You want to end your test?</h1>
        <hr>
        <button type="button" class="modal_btn" on:click={openScore}>CONFIRM</button>
        <button type="button" class="modal_btn" on:click={closeModal}>CANCEL</button>        
    </div>
</div>
{/if}

{#if showScore}
    <Score />
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
    .modal {
    position: fixed;
    top: calc(50% - 135px);
    left: calc(50% - 300px);
    height: 270px;
    width: 600px;
    background-color: rgb(50, 105, 105);
    z-index: 9999;
    }
</style>


















<!-- 
{#if showModal}
<div class="backdrop"></div>
    <div class="modal">
        <i class='bx bx-question-mark bx-tada' ></i>
        <h1>You want to end your test?</h1>
        <hr>
        <button type="button" class="modal_btn" on:click={openScore}>CONFIRM</button>
        <button type="button" class="modal_btn" on:click={closeModal}>CANCEL</button>        
    </div>
{/if}

{#if showScore}
    <Score />
{/if} -->


<!-- 
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
.modal{
    position: fixed;
    top: calc(50% - 135px);
    left: calc(50% - 300px);
    height: 270px;
    width: 600px;
    background-color: #ffffff;
    z-index: 9999;
    border-radius: 5px;
    border-left: 5px solid rgb(128, 0, 0);
    }
.modal i {
    color: #ffffff; 
    font-size: 3rem;
    background-color: rgb(128, 0, 0);
    border-radius: 100px;
    margin: 50px 10px 10px 25px;
}
.modal h1 {
    display: inline;
    font-weight: 400;
    position: relative;
    top: -10px;
    font-size: 1.85rem;
}
hr {
    width: 80%;
    border: 0;
    height: 1px;
    background: #333;
    background-image: linear-gradient(to right, #ccc, #333, #ccc);
    margin-top: 30px;
    margin-bottom: 40px;
}
.modal_btn {
    width : 120px;
    border-radius: 20px;
    background-color: #ffffff;
    color : rgba(128, 0, 0);
    font-size: 1.05rem;
    padding: 0.6rem;
    margin-left: 20%;
    transition: all 0.5s;
    font-weight: 400;
}
.modal_btn:hover {
    background-color: rgb(128, 0, 0);
    color: #ffffff;
    transition: all 0.5s;
}
</style> -->