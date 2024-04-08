The first time the viewer is loaded a request must be sent to iabderrahmane.github.io/?long=**number**&lat=**number** with query params long and lat. 
## API

<pre> <b>function getPanoramaInfo()</b> -> {
	long: number, 
	lat: number, 
	pitch: number [-90, 90],
	heading: number [-180, 180]

}</pre>
<pre><b>function changeLocation( coords: {long: number, lat: number} ) -> void</b>
This function changes the panorama to an image that corresponds to <b>coords</b>. If there's no nearby image it'll default to the last one. 
changeLocation will update the currect Long/Lat if a nearby image is found but doesn't fully match the requested coords.
</pre>

## Handlers

Whenever the location/heading/pitch change a message "**viewUpdated**" is sent to the IOS app. It contains the following object  { 
	long: number, 
	lat: number, 
	pitch: number [-90, 90],
	heading: number [-180, 180] 
}

## Notes
This only works with IOS (for now).
Since the backend is not deployed yet all the data is mocked. for instance:<br>
when calling the viewer link iabderrahmane.github.io/?long=**number**&lat=**number**  you'll get image 1. <br> 
When calling changeLocation with long [45, inf[ and lat [25, inf[ you'll get image 2. <br>
When calling changeLocation with long [35, 45[ and lat [15, 25[ you'll get image 3. <br>
When calling changeLocation with long < 35 and lat < 15 you'll get an error response (which is the last viewed image).<br>
