<!-- <script>
    import { showSection } from '../store/list-store.js';
    import { onDestroy } from 'svelte';
    import { qReffrence } from '../store/questionRefference';

    // export let showSide;   
    let QA = [
		{
            "id": 1,
			"question": "Who invented JavaScript?",
			"answers": [ 
                "Douglas Crockford",
                "Sheryl Sandberg",
                "Brendan Eich"
			],
			"correctAnswer": 3,
            "status": false
		},
		{
            "id": 2,
			"question": "Which one of these is a JavaScript package manager?",
			"answers": [
                "Node.js",
                "TypeScript",
                "npm"
			],
			"correctAnswer": 3,
            "status": true
		},
		{
            "id": 3,
			"question": "Which tool can you use to ensure code quality?",
			"answers": [
                "Angular",
                "jQuery",
                "RequireJS",
                "ESLint"
			],
			"correctAnswer": 4,
            "status": false
		},
		{
            "id": 4,
			"question": "Which of the following are themselves a collection of different data types?",
			"answers": [
                "string",
                "structures",
                "char",
                "all of the mentioned"
			],
			"correctAnswer": 2,
            "status": false
		},
		{
            "id": 5,
			"question": "Which of the following cannot be a structure member?",
			"answers": [
                "Another structure",
                "Function",
                "Array",
                "None of the mentioned"
			],
			"correctAnswer": 2,
            "status": false
		},
		{
            "id": 6,
			"question": "User-defined data type can be derived by___________",
			"answers": [
                "struct",
                "enum",
                "typedef",
                "all of the mentioned"
			],
			"correctAnswer": 4,
            "status": false
		},
		{
            "id": 7,
			"question": "Which of the following is not a pointer declaration?",
			"answers": [
                "char a[10];",
                "char a[] = {‘1’, ‘2’, ‘3’, ‘4’};",
                "char *str;",
                "char a;"
			],
			"correctAnswer": 4,
            "status": false
		},
		{
            "id": 8,
			"question": "A variable declared in a function can be used in main().",
			"answers": [
                "True",
                "False",
                "True if it is declared static",
                "None of the mentioned;"
			],
			"correctAnswer": 2,
            "status": false
		},
		{
            "id": 9,
			"question": "The name of the variable used in one function cannot be used in another function.",
			"answers": [
                "True",
                "False",
			],
			"correctAnswer": 2,
            "status": false
		},
		{
            "id": 10,
			"question": "The format identifier ‘%i’ is also used for _____ data type.",
			"answers": [
                "char",
                "int",
                "float",
                "double"
			],
			"correctAnswer": 2,
            "status": false
		}
	];
    
    let showSide;

    const unsubscribe = showSection.subscribe((data) => {
        showSide = data;
    });

    onDestroy(unsubscribe);

    function closelist() {
        showSection.update((value) => {
            return false;
        });
    }

    // let questionpointer;
    // qReffrence.subscribe((data) => {
    //     questionpointer = data;
    // })

    // $:console.log(questionpointer);

    // const unsubscribe = listSection.subscribe((data) => {
    //     showSide = data;
    // });
    
    // onDestroy(unsubscribe);

    // function closeSide() {
    //     listSection.update((value) => {
    //         return false;
    //     });
    // }
    
    // function changeNumber(i) {
    //         qReffrence.update((value) => {
    //         value = i-1;
    //         return value;
            
    //     });
    // }

    function changeNumber(i) {
            qReffrence.update((value) => {
            value = i;
            return value;
            
        });
    }

</script>
 
<div class="sidepanel">
    <h1>Question's List</h1>
    <hr />

    <ul class="unordered_list">
        {#each QA as arrList }
        <li class="list_item">
            <div class="list_content" on:click={changeNumber(arrList.id)}>
                <p>{arrList.question}</p>
            </div>
        </li>
        {/each}
    </ul> 
    
</div>

<style>
    *{
        font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    }
    .sidepanel {
        margin-top: 3.5rem;
        display: block;
        padding: 1rem;
        width: 30%;
        height: 85vh;
        background: white;
        border-radius: 5px;
        z-index: 10;
        box-shadow: 0 2px 8px rgba(0,0,0,0.26);
        overflow-y: scroll;
    }

    ul {
        background-color: rgba(0,0,0,0.7);
        padding: 0;
        width: 100%;
    }
    li {
        padding: 0.5rem;
        margin: auto;
        font-size: 15px;
        list-style-type: none;
        color: whitesmoke;
    }
    /* .checkbox {
    height: 25px;
    width: 25px;
    margin-top: 7px;
    border:1px solid #000000;
    border-radius: 2px;
    } */
    /* .checked {
    height: 25px;
    width: 25px;
    margin-top: 7px;
    border:1px solid #000000;
    border-radius: 2px;
    } */
</style>
 -->














<script>
    import { showSection } from '../store/list-store.js';
    import { onDestroy } from 'svelte';
    import { qReffrence } from '../store/question-store.js';

    let showSide;

    const unsubscribe = showSection.subscribe((data) => {
        showSide = data;
    });

    onDestroy(unsubscribe);

    function closelist() {
        showSection.update((value) => {
            return false;
        });
    }
    
    function changePointerOne() {
        qReffrence.update((value) => {
            return 0;
        });

    }
    function changePointerTwo() {
        qReffrence.update((value) => {
            return 1;
        });
    }
    function changePointerThree() {
        qReffrence.update((value) => {
            return 2;
        });
    }
    function changePointerFour() {
        qReffrence.update((value) => {
            return 3;
        });
    }
    function changePointerFive() {
        qReffrence.update((value) => {
            return 4;
        });
    }
    function changePointerSix() {
        qReffrence.update((value) => {
            return 5;
        });
    }
    function changePointerSeven() {
        qReffrence.update((value) => {
            return 6;
        });
    }
    function changePointerEight() {
        qReffrence.update((value) => {
            return 7;
        });
    }
    function changePointerNine() {
        qReffrence.update((value) => {
            return 8;
        });
    }
    function changePointerTen() {
        qReffrence.update((value) => {
            return 9;
        });
    }
</script>

{#if showSide}
<div class="list">
    <button type="button" id="closebtn" class="btn btn-outline-danger my-2 ml-2" on:click={closelist}>CLOSE</button>

    <hr />
    
    <ul class="unordered_list">
        <li class="list_item">
            <div class="list_content" on:click={changePointerOne}>
                <div class="checkbox">
                </div>
                <h3>Question 1</h3>
            </div>
        </li>
        <li class="list_item">
            <div class="list_content" on:click={changePointerTwo}>
                <div class="checkbox">
                </div>
                <h3>Question 2</h3>
            </div>
        </li>
        <li class="list_item">
            <div class="list_content" on:click={changePointerThree}>
                <div class="checkbox">
                </div>
                <h3>Question 3</h3>
            </div>
        </li>
        <li class="list_item">
            <div class="list_content" on:click={changePointerFour}>
                <div class="checkbox">
                </div>
                <h3>Question 4</h3>
            </div>
        </li>
        <li class="list_item">
            <div class="list_content" on:click={changePointerFive}>
                <div class="checkbox">
                </div>
                <h3>Question 5</h3>
            </div>
        </li>
        <li class="list_item">
            <div class="list_content" on:click={changePointerSix}>
                <div class="checkbox">
                </div>
                <h3>Question 6</h3>
            </div>
        </li>
        <li class="list_item">
            <div class="list_content" on:click={changePointerSeven}>
                <div class="checkbox">
                </div>
                <h3>Question 7</h3>
            </div>
        </li>
        <li class="list_item">
            <div class="list_content" on:click={changePointerEight}>
                <div class="checkbox">
                </div>
                <h3>Question 8</h3>
            </div>
        </li>
        <li class="list_item">
            <div class="list_content" on:click={changePointerNine}>
                <div class="checkbox">
                </div>
                <h3>Question 9</h3>
            </div>
        </li>
        <li class="list_item">
            <div class="list_content" on:click={changePointerTen}>
                <div class="checkbox">
                </div>
                <h3>Question 10</h3>
            </div>
        </li>
    </ul>
</div>
{/if}



<style>
.list {
    position: fixed;
    top: 7rem;
    bottom: 4.1rem;
    left: 0;
    height: 33rem;
    width: 300px;
    background-color: #ffffff;
    z-index: 9990;
    border-right: 3px solid rgb(128, 0, 0);
    overflow-y: scroll;
}
.list #closebtn {
    font-size: 1rem;
    position: absolute;
    left: 0;
}
.unordered_list {
    list-style-type: none;
    margin-top: 1rem;
}

.list_content {
    display: flex;
    margin: 20px 0px 20px 0px;
}
.list_content h3 {
    font-weight: 400;
    padding: 0;
    font-size: 1.75rem;
    margin: 0px 40px 0px 15px;
}
.checkbox {
    height: 25px;
    width: 25px;
    margin-top: 7px;
    border:1px solid #000000;
    border-radius: 50%;
}

hr {
    border: 2px double red;
    margin-top: 4rem;
}
</style>