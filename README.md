The first time the viewer is loaded a request must be sent to with query params long and lat. 
## API

**function getPanoramaInfo()** -> { 
	long: number, 
	lat: number, 
	pitch: number [-90, 90],
	heading: number [-180, 180] 
}
**function changeLocation( coords: {long: number, lat: number} )** -> void
This function changes the panorama to an image that corresponds to **coords**. If there's no nearby image it'll default to the last one. 
**

## Handlers

Whenever the location/heading/pitch change a message "viewUpdated" is sent to the IOS app. It contains the following object  { 
	long: number, 
	lat: number, 
	pitch: number [-90, 90],
	heading: number [-180, 180] 
}

## Notes
This only works with IOS no Android yet.