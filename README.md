# Daily Python Practice with ChatGPT, Claude & Meta AI (WhatsApp)
<b>Reservoir Management Report</b>
```python
reservoirs = {
    "Tilaiya":      {"storage": [62, 68, 71, 75],
                     "release": [18, 20, 19, 22]},
    "Maithon":      {"storage": [81, 85, 88, 90],
                     "release": [25, 28, 26, 30]},
    "Panchet":      {"storage": [74, 76, 79, 82],
                     "release": [21, 23, 22, 24]},
    "Konar":        {"storage": [45, 48, 50, 52],
                     "release": [14, 15, 13, 16]},
    "Mukutmanipur": {"storage": [92, 95, 94, 96],
                     "release": [30, 32, 31, 33]},
    "Durgapur":     {"storage": [55, 58, 60, 62],
                     "release": [17, 18, 19, 20]}
}
```
<b>Mission</b>
```python
def reservoir_report(reservoirs):
```
<b>Step 1</b><br>
For each reservoir calculate:</br>
<ul>
<li>Average Storage
<li>Average Release
</ul>

<b>Step 2</b><br>
A reservoir is <b>"Critical"</b> if:<br>
```
Average Storage >= 60
AND
Average Release >= 25
```
Otherwise -> <b>"Normal"</b><br>

<b>Step 3</b><br>
For <b>critical</b> reservoirs only:<br>
store:<br>
```python
{
     "Average Storage":....
     "Average Release":....
     "Status":"Critical"
}
```
<b>Step 4</b><br>
While looping through Critical reservoirs keep track of:<br>
<ul>
<li>total average storage
<li>number of Critical reservoirs
<li>reservoir with the highest average storage
</ul>

<b>Step 5</b><br>
After the loop calculate:<br>
<ul>
<li>Overall average storage of critical reservoirs
</ul>

<b>Return</b><br>
```python
{
    "report": report,
    "statistics": {
        "Critical Reservoirs": ...,
        "Overall Average Storage": ...,
        "Highest Storage Reservoir": ...,
        "Highest Storage Average": ...
    }
}
```

# Solution:
```python
reservoirs = {
    "Tilaiya": {"storage": [62, 68, 71, 75], 
                "release": [18, 20, 19, 22]},
    "Maithon": {"storage": [81, 85, 88, 90], 
                "release": [25, 28, 26, 30]},
    "Panchet": {"storage": [74, 76, 79, 82], 
                "release": [21, 23, 22, 24]},
    "Konar": {"storage": [45, 48, 50, 52], 
              "release": [14, 15, 13, 16]},
    "Mukutmanipur": {"storage": [92, 95, 94, 96], 
                     "release": [30, 32, 31, 33]},
    "Durgapur": {"storage": [55, 58, 60, 62], 
                 "release": [17, 18, 19, 20]}
}
def myfunction(reservoirs):
    result = {}
    total = 0
    count = 0
    highest = 0
    highest_mean_station = 0
    total_average_storage = 0
    critical_reservoir = []
    for reservoir, data in reservoirs.items():
        average_storage = sum(data["storage"]) / len(data["storage"])
        average_release = sum(data["release"]) / len(data["release"])
        if average_storage >= 80 and average_release >= 25:
            result[reservoir] = {"Average Storage":average_release,
                                 "Average Release":average_storage,
                                 "Status":"Critical"}
            critical_reservoir.append(reservoir)
            total_average_storage += average_storage
            count += 1
            overall_average = total_average_storage / count
            if highest is None or average_storage > highest:
                highest = average_storage
                highest_mean_station = reservoir
        else:
            result[reservoir] = {"Average Storage":average_release,
                                 "Average Release":average_storage,
                                 "Status":"Normal"}
    return f"{result}",f"Critical Reservoirs: {critical_reservoir}",f"Overall Average Storage: {overall_average}",f"Highest Storage Reservoir: {highest_mean_station}",f"Highest Storage Average: {highest}"
print(myfunction(reservoirs))
```
# Output:
```
("{'Tilaiya': {'Average Storage': 19.75, 'Average Release': 69.0, 'Status': 'Normal'}, 'Maithon': {'Average Storage': 27.25, 'Average Release': 86.0, 'Status': 'Critical'}, 'Panchet': {'Average Storage': 22.5, 'Average Release': 77.75, 'Status': 'Normal'}, 'Konar': {'Average Storage': 14.5, 'Average Release': 48.75, 'Status': 'Normal'}, 'Mukutmanipur': {'Average Storage': 31.5, 'Average Release': 94.25, 'Status': 'Critical'}, 'Durgapur': {'Average Storage': 18.5, 'Average Release': 58.75, 'Status': 'Normal'}}", "Critical Reservoirs: ['Maithon', 'Mukutmanipur']", 'Overall Average Storage: 90.125', 'Highest Storage Reservoir: Mukutmanipur', 'Highest Storage Average: 94.25')
PS C:\Users\hp\Downloads\sql_practice(0)>
```
