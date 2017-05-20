# Vehicule-data-API
JSON based API, easy to use for retrieving detailed car information from VehiculeDataService, including year, make, model, full model name, production end, and entire car specifications. Using Vehicule Data API is as simple as including a javascript file, It all about including a simple javascript file and few lines of code in your html page.


## Getting Started

##### Easy to integrate, easy to use

1. Include the jquery.min.js and the jquery.CarData.0.1.1.js in your document.
```
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>
<script type="text/javascript" src="http://www.themeleger.com/api/jquery.CarData.0.1.1.js"></script>
```

2. Document .ready event must init CarData Object
```
<script type="text/javascript">
    $(document).ready(
        function() {
            var cardata = new CarData();
            cardata.init();
        }
    )
</script>
```

3. Once Object initialised, we must pass html component's id(s) to the CarData Object and init "Show Data" data with it's event that fire data generation in the passed id
```
cardata.idInitialiser('year', 'maker', 'model', 'trim','message');
$('#bt-show-data').click(  function(){ cardata.generateCarData('data-container'); } );
```

4. Create the HTML select elements that will be contain generated data by the API. IDs must be set according to the values used in the cardata.idInitialiser called in step 3.
```
<div>
  <select name="year" id="year"></select>  
	<select name="maker" id="maker"></select> 
	<select name="model" id="model"></select>
	<select name="trim" id="trim"></select> 
</div>
```

5. This button when clicked (3.),  will generate selected model data in the given container as a table as well as message container for error handling
```
  <input id="bt-show-data" type="button" value="Show Data" />
	<div id="message" style="color : red;"></div> 
	<div id="data-container"></div> 
```

6. And the table where data will be shown
```
<table> 
		<tr> 
			<td valign="top"><div id="maker-list" /></td> 
			<td valign="top"><div id="model-list" /></td> 
			<td valign="top"><div id="trim-list" /></td> 
		</tr> 
		<tr> 
			<td colspan="3"><div id="trim-data-list" /></td> 
		</tr> 
	</table> 
```

### INFO
- Built this API for self-purpose and thought of sharing it here.
- Feel free to contribute.
- You can check the vehicule-database that the service is calling here : https://github.com/WiildchiilD/Vehicule-data-DB
- Give our a blog a check : http://www.themeleger.com/
