# blurry-loading-html-css-javascript code 
<!DOCTYPE html>
<html lang="en">
<head>		
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
	<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="HandheldFriendly" content="true">
    <meta name = "format-detection" content = "telephone=no">
        
    <title>Blurry Loading</title>

	<!-- Styles -->
    <style>
        *{
    box-sizing: border-box;
}
body{
    font-family: 'Roboto', sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    overflow: hidden;
    margin: 0;
}
.main-bg{
    background: url(https://wallpapercave.com/wp/wp2624675.jpg) no-repeat;
    background-position: center;
    background-size: cover;
    position: absolute;
    top: -30px;
    left: -30px;
    width: calc(100vw + 60px);
    height: calc(100vh + 60px);
    z-index: -1;
    filter: blur(100px);
}
.loading-wrapper{
    background-color: #76652d;
    border-radius: 50%;
    width: 120px;
    height: 120px;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0px 0px 49px 30px rgba(92, 144, 139, 1);
}

.loading-text{
    font-size: 42px;
    color: #fff;
}
    </style>

</head>
<body>
<section class="main-bg"></section>
<div class="loading-wrapper">
    <div class="loading-text">0%</div>
</div>

    


 <!-- Scripts -->
 <script>
     const bg = document.querySelector('.main-bg');
const loadingWrapper = document.querySelector('.loading-wrapper');
const loadingText = document.querySelector('.loading-text');

let loader = 0;
let count = setInterval(blurring, 60);

function blurring(){
    loader++;

    if(loader > 99){
        clearInterval(count);
    }

    loadingText.innerText = `${loader}%`;
    loadingText.style.opacity = scale(loader, 0, 100, 1, 0);
    loadingWrapper.style.opacity = scale(loader, 0, 100, 1, 0);
    bg.style.filter = `blur(${scale(loader, 0, 100, 30, 0)}px)`;
}

const scale = (num, in_min, in_max, out_min, out_max) => {
    return (num - in_min) * (out_max - out_min) / (in_max - in_min) + out_min;
}
 </script>
</body>  
</html>
