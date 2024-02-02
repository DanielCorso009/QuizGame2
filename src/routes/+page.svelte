<script>
    let score = 0;
    let questions = [
       {
         question: "What is the capital of France?",
         answers: ["Paris", "London", "Berlin", "Madrid"],
         correctAnswer: "Paris"
       },
       // More questions...
    ];
    let selectedAnswers = {};
   
    function handleClick(questionIndex, answer) {
       selectedAnswers[questionIndex] = answer;
       handleSubmit();
    }
   
    function handleSubmit() {
       let tempScore = 0;
       for (let i = 0; i < questions.length; i++) {
         if (selectedAnswers[i] === questions[i].correctAnswer) {
           tempScore++;
         }
       }
       score = tempScore;
    }
   </script>
   
   <main>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Lobster+Two&display=swap" rel="stylesheet">
    <h1>Quiz Game</h1>
    <form on:submit|preventDefault={handleSubmit}>
       <h2>Score: {score}</h2>
       {#each questions as question, index (question.question)}
         <h2>{question.question}</h2>
         <div class="grid">
           {#each question.answers as answer (answer)}
             <button on:click|preventDefault={() => handleClick(index, answer)}>{answer}</button>
           {/each}
         </div>
       {/each}
    </form>
   </main>
   
   <style>
    :root {
        background-color: #2d2b30;
    }

    main {
       color: white;
       font-family: 'Roboto', sans-serif;
       text-align: center;
       padding: 1em;
       max-width: 240px;
       margin: 0 auto;
    }
   
    h1 {
       color: #e86577;
       text-transform: uppercase;
       font-family: 'Lobster Two', sans-serif;
       font-size: 2em;
       font-weight: 100;
    }
   
    .grid {
       display: grid;
       grid-template-columns: repeat(2, 1fr);
       gap: 10px;
    }
   
    button {
       background: #e86577;
       color: white;
       font-family: 'Roboto', sans-serif;
       border: solid;
       border-width: 1px;
       border-radius: 5px;
       padding: 1em;
       cursor: pointer;
       transition: background 0.3s ease;
    }
   
    button:hover {
       background: darkred;
    }
   
    button:disabled {
       background: grey;
       cursor: not-allowed;
    }
   </style>
   