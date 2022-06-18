## Habit Tracker
- [ ] Refresh 

```dataview
TABLE WITHOUT ID
	link(file.name) as "日期",
	Reading AS "🌄",
	Birds AS "🐥",
	Workout AS "🏃‍♂️",
	E-mail AS "💌",
	Writing AS "📝",
	Mood AS "👾",
	Summary
	FROM "00 - DailyNotes/DailyNote" 
	SORT file.name DESC
	LIMIT 7
```


``` tracker
searchType: dvField
searchTarget: sleep
folder: Periodic notes
startDate: 2022-05-17

line:
    title: "Sueñito"
    xAxisLabel: Day
    yAxisUnit: h
    yAxisLabel: Tiempo
```

endDate: `$=file.mtime`
``` tracker
searchType: tag
searchTarget: tagName
folder: /
startDate:
endDate:
summary:
    template: "Average value of tagName is {{average}}"
    style: "color:white;"
```

```tracker
searchType: dvField
searchTarget: sleep
folder: Periodic notes
summary:
    template: "Longest Streak: {{maxStreak()}} day\nLongest Breaks: {{maxBreaks()}} day(s)\nLast streak: {{currentStreak()}} day(s)"
```


```tracker
searchType: dvField
searchTarget: sleep
datasetName: Sueñito
folder: Periodic notes
month:
    startWeekOn: 'Sun'
    threshold: 2
    color: grey
    headerMonthColor: orange
    dimNotInMonth: true
    selectedRingColor: steelblue
    showSelectedValue: true
```
****


```dataviewjs 

```
### Alcohol Consumption
```dataviewjs
dv.span("**🍺 Alcohol Consumption 🍺**")

const calendarData = {
    year: 2022,
    colors: {
        blue: ["#ffdf04","#ffbe04","#ff9a03","#ff6d02","#ff2c01"]
    },
    entries: [] 
}

for(let page of dv.pages('"daily notes"').where(p=>p.alcohol).sort(p=>p.file.name)){
	//dv.paragraph(page.file.name + " Alcohol units: " + page.alcohol)
    
    calendarData.entries.push({
        date: page.file.name,
        intensity: page.alcohol
    })  
}

renderHeatmapCalendar(this.container, calendarData)
```

```dataviewjs
dv.span("**Writing - Dont break the chain! 🔗🔗**")

const calendarData = {
    year: 2022,
    colors: {
        white: ["#fff","#fff","#fff","#fff","#fff"],
    },
    entries: []
}

for(let page of dv.pages('"daily notes"').where(p=>p.writing).sort(p=>p.file.name)){
	 
    calendarData.entries.push({
        date: page.file.name,
        intensity: 5,
        content: "🔗"
    })   
}

//console.log(calendarData)
	
renderHeatmapCalendar(this.container, calendarData)
```

```dataviewjs
dv.span("**🏋️ Exercise 🏋️**")

const calendarData = {
    year: 2022,
    colors: {
        red: ["#ff9e82","#ff7b55","#ff4d1a","#e73400","#bd2a00"]
    },
    entries: []
}

for(let page of dv.pages('"Periodic notes"').where(p=>p.workout).sort(p=>p.file.name)){
    calendarData.entries.push({
        date: page.file.name,
        intensity: page.workout
    })
       
}

renderHeatmapCalendar(this.container, calendarData)
```

```dataviewjs
dv.span("**🏋️ Sleep 🏋️**")

const calendarData = {
    year: 2022,
    entries: []
}

for(let page of dv.pages('"Periodic notes"').where(p=>p.sleep).sort(p=>p.file.name)){
    calendarData.entries.push({
        date: page.file.name,
        intensity: page.sleep
    })
       
}

renderHeatmapCalendar(this.container, calendarData)
```

```dataviewjs
dv.span("**🍺 Alcohol Consumption 🍺**")

const calendarData = {
    year: 2022,
    colors: {
        blue: ["#ffdf04","#ffbe04","#ff9a03","#ff6d02","#ff2c01"]
    },
    entries: [] 
}

for(let page of dv.pages('"daily notes"').where(p=>p.alcohol).sort(p=>p.file.name)){
	//dv.paragraph(page.file.name + " Alcohol units: " + page.alcohol)
    
    calendarData.entries.push({
        date: page.file.name,
        intensity: page.alcohol
    })  
}

renderHeatmapCalendar(this.container, calendarData)
```



```dataviewjs
dv.span("**🦷 Tooth Higyene 🌊**")

const calendarData = {
    year: 2022,
    colors: {
        red: ["#ff9e82","#ff7b55","#ff4d1a","#e73400","#bd2a00"], 
		green: ["#c6e48b","#7bc96f","#49af5d","#2e8840","#196127"]
    },
    entries: [] 
}


for(let page of dv.pages('"daily notes"').where(p=>p.alcohol).sort(p=>p.file.name)){
	//dv.paragraph(page.file.name + " Alcohol units: " + page.alcohol)
    
    calendarData.entries.push({
        date: page.file.name,
        intensity: page.alcohol
        color: "red",
        
    })  
}

renderHeatmapCalendar(this.container, calendarData)
```


colors: { // (optional) Defaults to green 
blue: ["#8cb9ff","#69a3ff","#428bff","#1872ff","#0058e2"], 
green: ["#c6e48b","#7bc96f","#49af5d","#2e8840","#196127"], 
red: ["#ff9e82","#ff7b55","#ff4d1a","#e73400","#bd2a00"], 
orange: ["#ffa244","#fd7f00","#dd6f00","#bf6000","#9b4e00"], 
pink: ["#ff96cb","#ff70b8","#ff3a9d","#ee0077","#c30062"], 
orangeToRed: ["#ffdf04","#ffbe04","#ff9a03","#ff6d02","#ff2c01"] 
}