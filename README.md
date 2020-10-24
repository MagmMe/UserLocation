## How to locate User in Swift using `CLLocationMaganer` protocol. 

Using `CLLocationManager` protocol you are able to track user on his IPhone. 

1. First things first. 

Add `MapView` to `Main.storyboard` an then create instance of it in `ViewController`

Choosing `YourProject.xcodeproject` Go to `Build Phases` then choose `Link Binary With Libraries`
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
`var locationManager = CLLocationManager()`

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

6. Fire up an aplication. In console / debugging area You can see longitude and latitude of your location. 

### TIP: If you want to simulate movement on you IPhone. 
Go to `Simulator` -> `Features` and choose: City Run, City Bike, FreeWayDrive

7. In function `locationManager` create variable which stores Users position. 

` let userLocation: CLLocation = locations[0]`

8. Then we need longitude and latitude which holds user position. 

`let latitide = userLocation.coordinate.latitude`
`let longitude = userLocation.coordinate.longitude` 

9. Import Map Kit and add `MKMapViewDelegate` protocol to `ViewController`

10. Add MapCoortinates to `ViewController` which dipslay user location on Map. 

`
let latDelta: CLLocationDegrees = 0.05
let longDelta: CLLocationDegrees = 0.05
        
let span = MKCoordinateSpan(latitudeDelta: latDelta, longitudeDelta: longDelta)
        
let location = CLLocationCoordinate2D(latitude: latitide, longitude: longitude)
        
let region = MKCoordinateRegion(center: location, span: span)
        
self.mapView.setRegion(region, animated: true)

`




