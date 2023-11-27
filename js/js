const api = '3e278f108e544776cb27a5789a12f619';
const iconImg = document.getElementById('weather-icon');
const loc = document.querySelector('#location');
const tempC = document.querySelector('.c');
const tempF = document.querySelector('.f');
const desc = document.querySelector('.desc');

const humidity1 = document.querySelector('.humidity');
const windspeed = document.querySelector('.windspeed');

const sunriseDOM = document.querySelector('.sunrise');
const sunsetDOM = document.querySelector('.sunset');

const cityInput = document.getElementById('city-input');

cityInput.addEventListener('keydown', (e) => {
    if (e.key === 'Enter') {
        const city = cityInput.value;
        const base = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${api}&units=metric&lang=ru`;
        fetch(base)
            .then((response) => {
                return response.json();
            })
            .then((data) => {
                const { temp, humidity} = data.main;
                const place = data.name;
                const {speed} = data.wind;
                const { description, icon } = data.weather[0];
                const { sunrise, sunset } = data.sys;

                const iconUrl = `http://openweathermap.org/img/wn/${icon}@2x.png`;
                const fahrenheit = (temp * 9) / 5 + 32;

                const sunriseGMT = new Date(sunrise * 1000);
                const sunsetGMT = new Date(sunset * 1000);
                iconImg.src = iconUrl;
                loc.textContent = `${place}`;
                desc.textContent = `${description}`;
                tempC.textContent = `${temp.toFixed(2)} °C`;
                tempF.textContent = `${fahrenheit.toFixed(2)} °F`;
                sunriseDOM.textContent = `${sunriseGMT.toLocaleDateString()}, ${sunriseGMT.toLocaleTimeString()}`;
                sunsetDOM.textContent = `${sunsetGMT.toLocaleDateString()}, ${sunsetGMT.toLocaleTimeString()}`;

                humidity1.textContent = `${humidity}%`;
                windspeed.textContent = `${speed} м/c`;
                
            });
            
    }
});
