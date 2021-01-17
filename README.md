# Delivery-Route-Planner
Given a list of addresses in Toronto, this planner can generate the most efficient (shortest) route and output as excel file.

<hr>

> "The ``travelling salesman problem (TSP)`` asks the following question: "Given a list of cities and the distances between each pair of cities, what is the shortest possible route that visits each city and returns to the origin city?" It is an **NP-hardproblem** in **combinatorial optimization**." -- by Wikipedia

## Input

* A list is imported by external file sources.
* A random list of addresses in Toronto with the home address as the starting and ending points:

```python
places = [
    "375 Bamburgh Cir, Scarborough, ON",
    "10231 Yonge St, Richmond Hill, ON",
    "1383 16th Ave, Richmond Hill, ON",
    "11 Disera Dr, Thornhill, ON",
    "280 West Beaver Creek Rd, Richmond Hill, ON",
    "3760 Hwy 7, Unionville, ON",
    "300 John St, Thornhill, ON",
    "5418 Yonge St #12, North York, ON",
    "8 William Kitchen Rd A, Scarborough, ON",
    "7575 Keele St, Concord, ON",
    "5284 Hwy 7, Markham, ON",
    "4205 Keele St, North York, ON",
    "3203 Dufferin St, North York, ON",
    "3400 Yonge St, Toronto, ON",
    "51 Gerry Fitzgerald Dr, Toronto, ON"
]
```

## TSP Solver

* By using ORtools from Google, the TSP question was solved to get the sub-optimal result by using distance matrix as the input.

```
Total distance: 98568 meters
Index:
 0 -> 5 -> 10 -> 4 -> 6 -> 2 -> 1 -> 3 -> 14 -> 9 -> 11 -> 12 -> 13 -> 7 -> 8 -> 0
```

## Optimal Route Output

* A dataframe was generated in the order of delivery spots, including address, lat, lng and maps url which can be clicked on a cellphone to navigate directly:

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>loc_id</th>
      <th>address</th>
      <th>latitude</th>
      <th>longitude</th>
      <th>maps_url</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>375 Bamburgh Cir, Scarborough, ON</td>
      <td>43.815527</td>
      <td>-79.322101</td>
      <td>https://www.google.com/maps/dir/?api=1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5</td>
      <td>3760 Hwy 7, Unionville, ON</td>
      <td>43.856633</td>
      <td>-79.332561</td>
      <td>https://www.google.com/maps/dir/?api=1&destination=3760+Hwy+7,+Unionville,+ON&travelmode=driving</td>
    </tr>
    <tr>
      <th>2</th>
      <td>10</td>
      <td>5284 Hwy 7, Markham, ON</td>
      <td>43.868385</td>
      <td>-79.283161</td>
      <td>https://www.google.com/maps/dir/?api=1&destination=5284+Hwy+7,+Markham,+ON&travelmode=driving</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>280 West Beaver Creek Rd, Richmond Hill, ON</td>
      <td>43.844163</td>
      <td>-79.387734</td>
      <td>https://www.google.com/maps/dir/?api=1&destination=280+West+Beaver+Creek+Rd,+Richmond+Hill,+ON&travelmode=driving</td>
    </tr>
    <tr>
      <th>4</th>
      <td>6</td>
      <td>300 John St, Thornhill, ON</td>
      <td>43.820492</td>
      <td>-79.398466</td>
      <td>https://www.google.com/maps/dir/?api=1&destination=300+John+St,+Thornhill,+ON&travelmode=driving</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2</td>
      <td>1383 16th Ave, Richmond Hill, ON</td>
      <td>43.861279</td>
      <td>-79.389934</td>
      <td>https://www.google.com/maps/dir/?api=1&destination=1383+16th+Ave,+Richmond+Hill,+ON&travelmode=driving</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1</td>
      <td>10231 Yonge St, Richmond Hill, ON</td>
      <td>43.876931</td>
      <td>-79.438363</td>
      <td>https://www.google.com/maps/dir/?api=1&destination=10231+Yonge+St,+Richmond+Hill,+ON&travelmode=driving</td>
    </tr>
    <tr>
      <th>7</th>
      <td>3</td>
      <td>11 Disera Dr, Thornhill, ON</td>
      <td>43.810779</td>
      <td>-79.453600</td>
      <td>https://www.google.com/maps/dir/?api=1&destination=11+Disera+Dr,+Thornhill,+ON&travelmode=driving</td>
    </tr>
    <tr>
      <th>8</th>
      <td>14</td>
      <td>51 Gerry Fitzgerald Dr, Toronto, ON</td>
      <td>43.784834</td>
      <td>-79.471775</td>
      <td>https://www.google.com/maps/dir/?api=1&destination=51+Gerry+Fitzgerald+Dr,+Toronto,+ON&travelmode=driving</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>7575 Keele St, Concord, ON</td>
      <td>43.796424</td>
      <td>-79.497674</td>
      <td>https://www.google.com/maps/dir/?api=1&destination=7575+Keele+St,+Concord,+ON&travelmode=driving</td>
    </tr>
    <tr>
      <th>10</th>
      <td>11</td>
      <td>4205 Keele St, North York, ON</td>
      <td>43.773829</td>
      <td>-79.492095</td>
      <td>https://www.google.com/maps/dir/?api=1&destination=4205+Keele+St,+North+York,+ON&travelmode=driving</td>
    </tr>
    <tr>
      <th>11</th>
      <td>12</td>
      <td>3203 Dufferin St, North York, ON</td>
      <td>43.718606</td>
      <td>-79.455361</td>
      <td>https://www.google.com/maps/dir/?api=1&destination=3203+Dufferin+St,+North+York,+ON&travelmode=driving</td>
    </tr>
    <tr>
      <th>12</th>
      <td>13</td>
      <td>3400 Yonge St, Toronto, ON</td>
      <td>43.732653</td>
      <td>-79.404582</td>
      <td>https://www.google.com/maps/dir/?api=1&destination=3400+Yonge+St,+Toronto,+ON&travelmode=driving</td>
    </tr>
    <tr>
      <th>13</th>
      <td>7</td>
      <td>5418 Yonge St #12, North York, ON</td>
      <td>43.775507</td>
      <td>-79.414727</td>
      <td>https://www.google.com/maps/dir/?api=1&destination=5418+Yonge+St+#12,+North+York,+ON&travelmode=driving</td>
    </tr>
    <tr>
      <th>14</th>
      <td>8</td>
      <td>8 William Kitchen Rd A, Scarborough, ON</td>
      <td>43.771816</td>
      <td>-79.280174</td>
      <td>https://www.google.com/maps/dir/?api=1&destination=8+William+Kitchen+Rd+A,+Scarborough,+ON&travelmode=driving</td>
    </tr>
    <tr>
      <th>15</th>
      <td>0</td>
      <td>375 Bamburgh Cir, Scarborough, ON</td>
      <td>43.815527</td>
      <td>-79.322101</td>
      <td>https://www.google.com/maps/dir/?api=1</td>
    </tr>
  </tbody>
</table>


## Google Maps API

* A map of all places are drawn on Google Maps:

<img src="https://github.com/kk-deng/Delivery-Route-Planner/blob/main/gmaps_route.png">

* With Google Directions API, we can plot the actual routes on the map. However, due to a large number of direction requests. The screenshot is not the final result.

<img src="https://github.com/kk-deng/Delivery-Route-Planner/blob/main/gmaps_actual.png">

```
Lengend for the map:
1  =  375 Bamburgh Cir, Scarborough, ON
2  =  10231 Yonge St, Richmond Hill, ON
3  =  1383 16th Ave, Richmond Hill, ON
4  =  11 Disera Dr, Thornhill, ON
5  =  280 West Beaver Creek Rd, Richmond Hill, ON
6  =  3760 Hwy 7, Unionville, ON
7  =  300 John St, Thornhill, ON
8  =  5418 Yonge St #12, North York, ON
9  =  8 William Kitchen Rd A, Scarborough, ON
10  =  7575 Keele St, Concord, ON
11  =  5284 Hwy 7, Markham, ON
12  =  4205 Keele St, North York, ON
13  =  3203 Dufferin St, North York, ON
14  =  3400 Yonge St, Toronto, ON
15  =  51 Gerry Fitzgerald Dr, Toronto, ON
```
