Remotely monitor the sensed temperature, humidity using DHT11 and also remotely control the fan (DC motor) speed using L293D.

### Requirements
* Raspberry Pi
* PHP + MYSQL for website
* Python
* DHT11 for temperature, humidity
* L293D to control DC motor speed.

### Installation

1. Make connections. You can make them as per the links provided in references.
2. Modify pin numbers utilized in `rpi.py`, only if needed.
3. `site` folder contains website code, deploy it and change the related URLs declared as `http://localhost/site/` in `rpi.py`, if needed.
4. Import `site/iot.sql` to setup database and it's tables with dummy data.
5. Update database credentials declared in `site/api/database.php`.
6. Run `rpi.py`

### Usage and Screenshots

1. Home page: `site/index.html`
![Home Screen](https://i.snag.gy/zVjRWa.jpg)

2. Show captured humidity, temperature: `site/data.html`
![Data List](https://i.snag.gy/sWlneP.jpg)

3. The graph on the same page, for comparison of humidity, temperature with reference to time.
![Graph](https://i.snag.gy/EXeGjC.jpg)

4. Display previous automatic setting parameters and change them: `site/settings.html`
![Auto Setting](https://i.snag.gy/CylK4Z.jpg)

5. Display previous manual settings and change it, the same page.
![Manual Setting](https://i.snag.gy/YkedFs.jpg)

6. What is Auto & Manual Setting?

Auto takes 3 input pairs:

* Low humidity-temperature `(x1,y1)`
* Medium humidity-temperature `(x2,y2)`
* High humidity-temperature `(x3,y3)`

Compares these 3 input pairs with currently sensed Humidity-Temperature `(x,y)` pair by using a modified form of **Distance Formula** in order to decide the speed of the fan: low, medium or high speed. 

Example, if the distance is `(x,y)` and `(x1,y1)` is the lowest, then speed must be low.

Manual takes one single input out of:
* Low
* Medium
* High
* None

If None is set, then it utilizes the latest auto setting parameters to decide the speed of the fan, otherwise, the Manual setting is considered over Auto Setting.

### Other Contributors

* [Bhavik Parmar]( https://github.com/bp1807)
* [Raj Nandu]( https://github.com/raj-nandu)

### References
* [DHT11]( http://www.circuitbasics.com/how-to-set-up-the-dht11-humidity-sensor-on-the-raspberry-pi/)
* [DC Motor Control using L293D - 1]( https://www.instructables.com/id/DC-Motor-Control-With-Raspberry-Pi-and-L293D/)
* [DC Motor Control using L293D - 2]( http://www.rhydolabz.com/wiki/?p=11288)