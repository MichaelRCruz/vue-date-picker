![](/datepicker.png)

## vue-date-picker

This is your basic date-picker application. You can hard code the range of dates in which you would like to allow the user to choose from. When the date is selected, the date is available as an object for any other perceivable use.

#### Installation Instructions

1. Fork or clone the repository.
```
git clone https://github.com/MichaelRCruz/vue-datepicker
```

2. Install all dependencies.
```
npm install
```

3. Fire up your server then point your browser to http://localhost:8080/
```
npm run dev
```

4. ...
```
...
```

5. Profit.

#### Usage

The end points of the date-range are set as Unix time stamps, e.g., 1494251559 seconds since January 1st, 1970. You can modify this range by hard-coding lines 61 & 62 of found in the file, `src/DatePicker.vue`.

```javascript

datesRange: [
              moment().subtract(1, 'week').unix(),
              moment().add(1, 'week').unix()
            ],

```

#### Challenges Faced

Date and time. Nuff said.

#### Technologies Used

* Vue.js
* Moment.js
* Node
* Bootstrap (form only)
