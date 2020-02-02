# Pavel Sashnikov

### Contacts:
- Phone: +375 29 613-37-06
- Email: Sashnikov24@gmail.com
- [Linkedin](https://linkedin.com/in/pavel-sashnikov-416470179/)
- Skype: live:7dedf76e23c5e03f

### Education:
- SkillUp (front-end development) 2018 - 2019
- Rolling Scopes School(RS2019-Q3)

### Skills:
1. __JS__
    - ES5
    - ES6
2. __HTML5__
3. __CSS3__
    - SASS (SCSS)
    - LESS
4. Version control: __GIT__
5. Frameworks: __Angular__
6. Methodologies: __BEM, mobile first, perfect pixel__

### Code examples:
 - [Weather](http://aggressive-person.surge.sh/)
 ```js
 export default class Location {
  constructor(weather, city, lang = 'en') {
    this.lang = lang;
  }

  getImage(weather) {
    let orientation = '';
    if (window.innerWidth >= window.innerHeight) {
      orientation = 'landscape';
    } else {
      orientation = 'portrait';
    }
    const key = '01191618e3c155db163a190e48794c7aeb22585231166c32184c3ad8f1ae2d9f';
    const url = `https://api.unsplash.com/photos/random?query=${this.city},${weather}&orientation=${orientation}&client_id=${key}`;

    return fetch(url)
      .then((res) => res.json());
  }

  getWeather() {
    const key = '321bd4115e6a23f2de2cd53fbfe836cd';
    const url = `https://api.openweathermap.org/data/2.5/forecast?q=${this.city}&lang=${this.lang}&units=metric&APPID=${key}`;

    return fetch(url)
      .then((res) => res.json());
  }

  getLocation() {
    const key = '10e75298a5ae53';
    const url = `https://ipinfo.io/json?token=${key}`;

    return fetch(url)
      .then((res) => res.json());
  }

  getData() {
    return this.getLocation().then((data) => {
      if (!this.city) {
        this.city = data.city;
      }
      return this.getWeather().then((weather) => Promise.all([Promise.resolve(weather), this.getImage(weather.list[0].weather[0].main)]));
    });
  }
}
 ```