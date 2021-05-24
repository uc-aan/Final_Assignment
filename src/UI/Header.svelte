<script>
	let logo = 'https://www.mangalmay.org/campusdriveucertify/images/logo.png';
</script>

<header>
	<div class="logoimage">
		<img src={logo} alt="uCertify">
	</div>
	<div class="content">
		<h1>uCertify Test Prep</h1>
	</div>
</header>


<style>
	header {
		position: fixed;
		width: 100%;
		top: 0;
		left: 0;
		height: 4rem;
		background-color: #cf0056;
		display: flex;
		justify-content: center;
		align-items: center;
		box-shadow: 0 2px 6px rgba(0,0,0,0.26);
		border: 1px solid black;
	}
    .logoimage {
		position: absolute;
		left: 0;
	
    }
    img {
		border-radius: 10px;
        width: 50%;
        height: 50%;
    }

	.content {
		position: absolute;
		color: white;		
		font-family: 'Courier New', Courier, monospace;
		margin: 0;
	}
</style>