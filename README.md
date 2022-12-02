<head> 
<meta charset="utf-8"> 
<title></title> 
	<style type="text/css">
	*,
*:before,
*:after{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}
		html,body{
		height:100%;
		}
body{
background: url(http://cdn.u1.huluxia.com/g4/M03/FA/79/rBAAdmOIG7OAOIW3AAFu6YMTqxM897.jpg) center center;
	background-size:cover;
}

}
    background:ur1(http://cdn.u1.huluxia.com/g4/M03/FA/79/rBAAdmOIG7OAOIW3AAFu6YMTqxM897.jpg);
}
.container{
    width: 40%;
    min-width: 450px;
    position: absolute;
    transform: translate(-50%,-50%);
    left: 50%;
    top: 50%;
    padding: 50px 30px;
}
.container *{
    font-family: "Poppins",sans-serif;
    border: none;
    outline: none;
}
.inputs-wrapper{
    background-color: #080808;
    padding: 30px 25px;
    border-radius: 8px;
    box-shadow: 0 15px 20px rgba(0,0,0,0.3);
    margin-bottom: 50px;
}
input,
button{
    height: 50px;
    background-color: #ffffff;
    color: #080808;
    font-weight: 500;
    border-radius: 5px;
}
input{
    width: 60%;
    padding: 0 20px;
    font-size: 14px;
}
button{
    width: 30%;
    float: right;
}
.outputs-wrapper{
    width: 100%;
    display: flex;
    justify-content: space-between;
}
.outputs-wrapper div{
    height: 100px;
    width: 100px;
    background-color: #080808;
    border-radius: 5px;
    color: #ffffff;
    display: grid;
    place-items: center;
    padding: 20px 0;
    box-shadow: 0 15px 20px rgba(0,0,0,0.3);
 
}
span{
    font-size: 30px;
    font-weight: 500;
}
p{
    font-size: 14px;
    color: #707070;
    font-weight: 400;
}

		h1{
		 text-align:center;
		
		
		}
	
	
	
	</style>
	<script>
	
	const months = [31,28,31,30,31,30,31,31,30,31,30,31];

function ageCalculate(){
    let today = new Date();
    let inputDate = new Date(document.getElementById("date-input").value);
    let birthMonth,birthDate,birthYear;
    let birthDetails = {
        date:inputDate.getDate(),
        month:inputDate.getMonth()+1,
        year:inputDate.getFullYear()
    }
    let currentYear = today.getFullYear();
    let currentMonth = today.getMonth()+1;
    let currentDate = today.getDate();

    leapChecker(currentYear);

    if(
        birthDetails.year > currentYear ||
        ( birthDetails.month > currentMonth && birthDetails.year == currentYear) || 
        (birthDetails.date > currentDate && birthDetails.month == currentMonth && birthDetails.year == currentYear)
    ){
        alert("Not Born Yet");
        displayResult("-","-","-");
        return;
    }

    birthYear = currentYear - birthDetails.year;

    if(currentMonth >= birthDetails.month){
        birthMonth = currentMonth - birthDetails.month;
    }
    else{
        birthYear--;
        birthMonth = 12 + currentMonth - birthDetails.month;
    }

    if(currentDate >= birthDetails.date){
        birthDate = currentDate - birthDetails.date;
    }
    else{
        birthMonth--;
        let days = months[currentMonth - 2];
        birthDate = days + currentDate - birthDetails.date;
        if(birthMonth < 0){
            birthMonth = 11;
            birthYear--;
        }
    }
    displayResult(birthDate,birthMonth,birthYear);
}

function displayResult(bDate,bMonth,bYear){
    document.getElementById("years").textContent = bYear;
    document.getElementById("months").textContent = bMonth;
    document.getElementById("days").textContent = bDate;
}

function leapChecker(year){
    if(year % 4 == 0 || (year % 100 == 0 && year % 400 == 0)){
        months[1] = 29;
    }
    else{
        months[1] = 28;
    }
}

	
	
	
	</script>
	
	
</head>
<body>
	<h1>年龄计算器</h1>
<div class="container">
        <div class="inputs-wrapper">
            <input type="date" id="date-input">
            <button onclick="ageCalculate()">Calculate</button>
        </div>
        <div class="outputs-wrapper">
            <div>
                <span id="years">
                    -
                </span>
				
                <p>
                    年
                </p>
            </div>
            <div>
                <span id="months">
                    -
                </span>
                <p>
                    月
                </p>
            </div>
            <div>
                <span id="days">
                    -
                </span>
                <p>
                  日
                </p>
            </div>
        </div>
    </div>

</body>
