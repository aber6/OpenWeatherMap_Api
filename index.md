<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>OpenWeatherMap Api</title>
  <style>
    *{
    margin:0;
    padding: 0;
    box-sizing: border-box;
  }
  
  body{
    font-family: "Nunito",sans-serif;
    background: #f8f8f8;
  }
  
  .input{
    text-align: center;
    margin: 100px auto;
  }
  
  input[type="submit"]{
    padding: 15px 30px;
    background: #e7e7e7;
    border: none;
    border-radius: 1px;
    font-family: "Nunito",sans-serif;
    font-weight:bold;
    font-size: 20px;
  }
  
  .input input[type="text"]{
    width: 600px;
    height: 55px;
    padding: 5px 10px;
    background: #e7e7e7;
    border: none;
    border-radius: 1px;
    font-family: "Nunito",sans-serif;
    font-weight:bold;
    font-size: 20px;
  }
  
  .card{
    width: 50%;
    background: #e7e7e7;
    height: 40vh;
    margin: 50px auto;
    border-radius: 2px;
  }
  
  
  .close{
    float: right;
    margin-top: -2px;
    cursor: pointer;
    margin-right: 20px;
  }
  
  .card h1{
    padding: 5px 0;
    text-align: center;
  }
  
  .card p{
    text-align: center;
    margin:40px 0;
    font-size:20px;
  }
  </style>
</head>

<body>
    <!-- <div class="main">
    <div class="header">
      <h1>OpenWeatherMap API</h1>
      <p>Enter any city name in the input box below to get the data</p>
    </div> -->

    <div class="input">
        <input type="text" placeholder="Enter the city" class="input_text">
        <input type="submit" value="Submit" class="submit">
    </div>
    </div>

    <div class="container">
        <div class="card">
            <h1 class="name" id="name"></h1>
            <p class="temp"></p>
            <p class="clouds"></p>
            <p class="desc"></p>
        </div>
    </div>
  <script>
    var input = document.querySelector('.input_text');
var main = document.querySelector('#name');
var temp = document.querySelector('.temp');
var desc = document.querySelector('.desc');
var clouds = document.querySelector('.clouds');
var button= document.querySelector('.submit');


button.addEventListener('click', function(name){
fetch('https://api.openweathermap.org/data/2.5/weather?q='+input.value+'&appid=50a7aa80fa492fa92e874d23ad061374')
.then(response => response.json())
.then(data => {
  var tempValue = data['main']['temp']-273;
  var nameValue = data['name'];
  var descValue = data['weather'][0]['description'];

  main.innerHTML = nameValue;
  desc.innerHTML = "Desc - "+descValue;
  temp.innerHTML = "Temp - "+tempValue +" C";
  input.value ="";

})

.catch(err => alert("City name does not exist in database!"));
})    
  </script>
</body>

</html>
