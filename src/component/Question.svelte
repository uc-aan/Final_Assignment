<script>
    import { onDestroy } from 'svelte';
    import Footer from '../UI/Footer.svelte';
    import Score from './Score.svelte';
    import { qReffrence } from '../store/question-store.js';
    import { reviewStatus } from '../store/review-store.js';

    
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


    // the following code will create an "answers" array of length same as QA array and fill with null.
    let answers = new Array(QA.length).fill(null);

    
    let qNumber;
    const unsubscribe = qReffrence.subscribe((data) => {
        qNumber = data;
    });

    

    let showReview;
    const unsubscribeReview = reviewStatus.subscribe((data) => {
        showReview = data;
    });

    onDestroy(unsubscribeReview);

    let hideBox = false;
    function startQuiz() {
        hideBox = true;
        qReffrence.update((value) => {
            return 0;
        });
    }

    let attempted=0;
    function getScore() {
        let score = answers.reduce((acc,val,index) => { 
            if(QA[index].correctIndex == val) {
                return acc+1;
            }  
            return acc;
        },0);
        return (score/QA.length * 100)+"%";  
    }

    const countAttempt = () => {
        let i=0;
        while (i<answers.length) {
            if(answers[i] != null){
                attempted+=1;   
            }
            else {
                answers[i] = "UNATTEMPTED";
            } 
            i++;
        }
        return attempted;
    };

    function selectAnswer(i) {
        answers[qNumber]=i+1;
    }
    //this is done to avoid memory leakage
    onDestroy(unsubscribe);
</script>

<div class="Appcontainer">
    {#if qNumber == -1 }
        <div class="test_screen" class:clicked={hideBox}>
            <button id="start" class="btn btn-outline-success" on:click={startQuiz}>START QUIZ</button>
        </div>
    {:else if !(qNumber > answers.length-1)}
        <div class="quiz_screen">
            <div class="test_box">
                <h2>
                    QUESTION {QA[qNumber].id} : {QA[qNumber].question}
                </h2>
                <div class="option">
                    {#each QA[qNumber].answers as opt,i}
                    <ul>
                        <li>
                            <label class="container">
                                <input type="radio" on:click={() => {selectAnswer(i)}}  name="answers" disabled={showReview} checked={answers[qNumber]==null ? false : showReview ? false : 'checked'}/>{"    " + opt}
                                <span class="checkmark"></span>
                            </label>
                            
                        </li>
                    </ul>
                    {/each}
                </div>

                {#if showReview}
                <h2 class="{QA[qNumber].correctIndex == answers[qNumber] ? 'correct' : 'incorrect'}">
                    
                    <span>YOUR ANSWER : {answers[qNumber]}</span>
                </h2>
                
                {/if}
                
            </div>

                <Footer />
        </div>
    {:else}
        <div class="score_screen">
            {#if !showReview}
            <Score totalScore={getScore()} attempted={countAttempt()}/>
            {:else}
                <div class="greeting">
                    <h1>Better luck next time!</h1>
                </div>
            {/if}
        </div>
    {/if}
</div>

<style>
#start {
    position: fixed;
    height: 50px;
    width: 200px;
    border-radius: 10px;
    top: calc(50% - 25px);
    left: calc(50% - 70px);
    font-size: 1.4rem;
    font-weight: bolder;
}
.Appcontainer{
    width: 100%;
    height: 95vh;
    display: flex;
    justify-content: center;
    align-items: center;       
}
.test_screen{
    background-color: blanchedalmond;
    height: 85vh;
    margin-top: 3.5rem;
    width: 100%;
}
.test_box {
    position: fixed;
    top: 7.1rem;
    bottom: 4.9rem;
    left: 0.7rem;
    right:0.7rem;
    background-color: antiquewhite;
    border-radius: 5px;
}
.test_box h2{
    font-weight: 400;
    margin: 4rem 0 0 20rem;
    font-size:1.75rem;
}
   
.option ul li{
    background-color: #000000;
    width: 400px;
    padding: 5px 5px 5px 20px;
    border-radius: 25px;
    transition: all 0.5s;
}

.option ul{
    list-style-type: none;
    margin: 1rem 0 0 20rem;
    font-size: 1.5rem;
    color: #ffffff;
    font-weight: 300;
}
.clicked {
    display: none;
}
</style>