# location
using the google play services location api, your app can request the last known location of the user's device . use the fused location provider to retrieve the device's last known location . is one of the location apis in google play services . it manages the underlying location technlogy and provides a simple api so that can specify requirements at a high level.

## set up google play services
to access the fused location provider , your app development project must include google play services , download and install the google play servies , and add the library to your project.

## specify app permissions
apps whose features use location servies must request location permissions , depending on the use cases of those features.


________

## create location services
onCreate() method , create instance of the fused location provider client  :

```
private FusedLocationProviderClient fusedLocationClient;

@Override
protected void onCreate(Bundle savedInstanceState) {

   fuedLocationClient=LocationServices.getFusedLocationProviderClient(this);
   
   }
```

____________

## get the last known location

```
fusedLocationClient.getLastLocation()
      .addOnSuccessListener(this , new OnSuccessListener<Location>() {
      @Override
      public void onSuccess(Location location) [
           
           if(location != null) {
               // logic to handle location object
               }
               }
               });
```

the getLastLocation() returns a task that you can use to get a Location object with the latitude and longitude coordinates of geographic location . 

___________
## choose the best location estimate 
the fusedLocationProviderClient provides several methods to retrieve device location information :

-getLastLocation() gets a location estimate more quickly and minimizes battery useage that can be attributed to your app. the location information might be out of data , if no other clients have activly used location recently.

-getCurrentLocation() get a fresher , more accurate location more consitenyly , however , this method can cause active location computation to occur on the device.

this is the recommended way to get a fresh location , whenever possible , and is safer than alternatives like starting and manging location updates yourself using 
requestLocationUpdates().

________
   
