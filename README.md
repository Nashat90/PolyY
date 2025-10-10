# Multi-Axis Plot Demonstration using `polyY.plotly`

This script demonstrates how to visualize multiple Y-axes datasets from various domains — energy, oil and gas, weather, and combo plots — using the `polyY.plotly` module.  
Each example defines X and Y variables, color schemes, and plotting styles, all unified in one workflow for easy demonstration.

![Energy Consumption](https://github.com/Nashat90/PolyY/images/1.png)
![Oil and Gas Metrics](https://github.com/Nashat90/PolyY/images/2.png)
![Weather Metrics](https://github.com/Nashat90/PolyY/images/3.png)
![Combo Chart](https://github.com/Nashat90/PolyY/images/4.png)

# Example 1: Energy Industry Data
```python
import polyY.plotly as plot
import pandas as pd

elect = pd.read_csv(r"data\electricity_consumption_data.csv")
x = elect.timestamp
ys = ['power_kwh', 'voltage_v', 'current_a', 'temperature_c', 'reactive_power_kvar']
clrs = ["pink", "magenta", "green", "purple", "orange"]

figure = plot.MakeFigure("Power Consumption Metrics", "plotly_dark")
for i in range(5):
    figure.add_trace(x, elect[ys[i]].to_list(), name=ys[i], kind="line", color=clrs[i])
figure.get_figure().update_layout(width=1500, height=800)
```



# Example 2: Oil and Gas Data
```python
import polyY.plotly as plot
import pandas as pd

data = pd.read_csv(r"data\oil and gas.txt", sep="\t")
x = data.Time_Days
ys = ['Gas_Volume', 'Water_Volume_', 'Casing_Pressure_', 'Active_Pressure_', 'Line_Pressure_', 'Calculated_Sandface_Pressure_']
clrs = ["olive", "blue", "magenta", "red", "orange", "green"]

figure = plot.MakeFigure("Oil and Gas Production Metrics", "none")
for i in range(6):
    figure.add_trace(x, data[ys[i]].to_list(), name=ys[i], kind="line", color=clrs[i])
figure.get_figure().update_layout(width=1500, height=800)
```


# Example 3: Weather and Forecast Data
```python
import polyY.plotly as plot
import pandas as pd

data = pd.read_csv(r"data\weather_data_500.csv")
x = data.timestamp
ys = ['humidity_%', 'wind_speed_m_s', 'rainfall_mm', 'solar_radiation_w_m2', 'pressure_hpa', 'temperature_c']
clrs = ["blue", "orange", "green", "magenta", "red", "olive"]

figure = plot.MakeFigure("Weather and Forecast Metrics", "ggplot2")
for i in range(6):
    figure.add_trace(x, data[ys[i]].to_list(), name=ys[i], kind="line", color=clrs[i])
figure.get_figure().update_layout(width=1500, height=800)
```


# Example 4: Combo Chart
```python
import polyY.plotly as plot
import pandas as pd

data = pd.read_csv(r"data\oil and gas.txt", sep="\t")
x = data.Time_Days
ys = ['Gas_Volume', 'Water_Volume_', 'Casing_Pressure_', 'Active_Pressure_']
clrs = ["olive", "blue", "magenta", "red"]
types = ["area", "area", "line", "scatter"]

figure = plot.MakeFigure("Combo Chart Example", "none")
for i in range(4):
    figure.add_trace(x, data[ys[i]].to_list(), name=ys[i], kind=types[i], color=clrs[i])
figure.get_figure().update_layout(width=1500, height=800)

```
