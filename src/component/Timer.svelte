<script>
	
	let second = 90 * 60; // seconds
	let time = setInterval(clockTimer, 1000);

	function clockTimer() {
		let minutes = Math.floor(second / 60);
		let seconds = (second % 60);
		seconds = (seconds < 90) ? + seconds : seconds;
		minutes = (minutes < 90) ? + minutes : minutes;

		document.getElementById('clock').innerHTML = minutes+"  :  "+seconds;
		second--;

		if (second == -1) {
        clearInterval(clockTimer);
        alert("Time Up!");
        }
	}
	

</script>

<span id="timer"><svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 0 24 24" width="24px" fill="#FFFFFF"><path d="M0 0h24v24H0z" fill="none"/><path d="M15 1H9v2h6V1zm-4 13h2V8h-2v6zm8.03-6.61l1.42-1.42c-.43-.51-.9-.99-1.41-1.41l-1.42 1.42C16.07 4.74 14.12 4 12 4c-4.97 0-9 4.03-9 9s4.02 9 9 9 9-4.03 9-9c0-2.12-.74-4.07-1.97-5.61zM12 20c-3.87 0-7-3.13-7-7s3.13-7 7-7 7 3.13 7 7-3.13 7-7 7z"/></svg></span>
<span id="clock"></span>
<span id="sptxt">TIME</span>

<style>
    #clock{
        position: relative;
        top:2px;
        font-size : 1.5rem;
        color : #ffffff;
        font-weight: 500;
        width: 80px;
		display: flex;
		justify-content: center;
		align-items: center;
    }
	#sptxt{
		position: relative;
		font-weight: bold;
		color : #ffffff; 
		top:2px; 
		font-size : 1.3rem;   
		margin-right: 30px;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	#timer {
		display: flex;
		justify-content: center;
		align-items: center;
	}
</style>