## How to locate User in Swift using `CLLocationMaganer` protocol. 

Using `CLLocationManager` protocol you are able to track user on his IPhone. 

1. First things first. Choosing `YourProject.xcodeproject` Go to `Build Phases` then choose `Link Binary With Libraries`
and add framework, which display info for user to allow acces to track.  

Using `+` add `CoreLocation.framework` to library of your project. 

2. Go to `info.plist` choosing it from main menu of your project and add two rules: key-value. 
Right click, and `add row`. 

First Key:
`NSLocationWhileInUseUsageDescription`
as type `String` and `value` add sentence which will display to the user while fired aplication up. 
f.e: "I need to know your location"

Second Key:
`NSLocationAlwaysUsageDescription` as `String` type and value: "Add your info here". 

### Creating an App

1. Import `CoreLocation` then add protocol `CLLocationManagreDelagate` to your `ViewController`
2. Add variable which holds userlocation: 
`var locationManager - CLLocationManager()`

3. Add 
`
locationManager.delegate = self
locationManager.desiredAccuracy = kCLLocationAccuracyBest
`

4. Add properties to `locationManager` which could track user. 
`
locationManager.requestWhenInUseAuthorization()
locationManager.startUpdatingLocation()

5. Add method

`
func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
 print(locations)
    }
`

6. Fire Up Aplication. Now in console / debugging area You can see longitude and latitude of your location. 

### TIP: If you want to simulate movement on you IPhone. 
Go to `Simulator` -> `Features` and choose: City Run, City Bike, FreeWayDrive

7. Creating variable which stores Users position. 



