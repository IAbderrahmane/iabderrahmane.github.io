The first time the viewer is loaded a request must be sent to iabderrahmane.github.io/?long=**number**&lat=**number** with query params long and lat. 
## API

**function getPanoramaInfo()** -> { 
	long: number, 
	lat: number, 
	pitch: number [-90, 90],
	heading: number [-180, 180] 
}
**function changeLocation( coords: {long: number, lat: number} )** -> void
This function changes the panorama to an image that corresponds to **coords**. If there's no nearby image it'll default to the last one. 
changeLocation will update the currect Long/Lat if a nearby image is found but doesn't fully match the requested coords.
**

## Handlers

Whenever the location/heading/pitch change a message "viewUpdated" is sent to the IOS app. It contains the following object  { 
	long: number, 
	lat: number, 
	pitch: number [-90, 90],
	heading: number [-180, 180] 
}

## Notes
This only works with IOS (for now).
Since the backend is not deployed yet all the data is mocked. for instance:
when calling the viewer link iabderrahmane.github.io/?long=**number**&lat=**number**  you'll get image 1. 
When calling changeLocation with long [45, inf[ and lat [25, inf[ you'll get image 2.
When calling changeLocation with long [35, 45[ and lat [15, 25[ you'll get image 3.
When calling changeLocation with long < 35 and lat < 15 you'll get an error response (which is the last viewed image).
