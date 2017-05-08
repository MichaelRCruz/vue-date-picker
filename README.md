![](/datepicker.png)

## vue-date-picker

This is a date picker that only allows a certain range of dates to choose from. For this specific application, it's a range of two years, i.e., one full year preceding today's date and one full year following today's date. The chosen date is displayed in a generic form-field as a string, but the user's selected date object is still available for use in any programatic way.

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
              moment().subtract(1, 'year').unix(),
              moment().add(1, 'year').unix()
            ],

```

#### Challenges Faced

Date and time. Nuff said.

#### Technologies Used

* Vue.js
* Moment.js
* Node
* Bootstrap (form only)
