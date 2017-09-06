# Vehicule-data-API
JSON based API, easy to use for retrieving detailed car information from VehiculeDataService, including year, make, model, full model name, production end, and entire car specifications. Using Vehicule Data API is as simple as including a javascript file and few lines of code in your html page.


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

4. Create the HTML select elements that will contain generated data by the API. IDs must be set according to the values used in the cardata.idInitialiser called in step 3.
```
<div>
  <select name="year" id="year"></select>  
	<select name="maker" id="maker"></select> 
	<select name="model" id="model"></select>
	<select name="trim" id="trim"></select> 
</div>
```

5. The button when clicked (3.),  will generate selected model data in the given container as a table as well as message container for error handling
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

##### Init and use a search box
Note : In this demo, i used tag-it create an auto complete search box and this is how i did it
1. After creating CarData object in .ready function, you need to initialise with your input id

```
<input  id="in_search" type="button" value="search"\>
```

```
$('#in_search').click(  function(){ cardata.UISearch($("#mytags").tagit("assignedTags"),'data-container') } );
```

2. Create tags that will be shown with auto completetion 

```
$(document).ready(function() {
		$("#mytags").tagit(
		{
			availableTags: ["year =", "maker =", "model =", "fullmodelname =", "productionend ="],
			//you can extend this list depends on search tags you wish to provide ( 33 in all, available in the link to the database )
			allowSpaces :true,
		});
```
##### API Search with [?call=-]

You can request data from server in every possible way and you can filter and show specific or all information available

* Build your request using : - getData 
```
To return entire vehicule data
Minimal request parameter : 
https://cardata.000webhostapp.com/api.php/vehicule?call=getData&maker=kia

For every Kia model from 1800 to date

More parameter :
ie : https://cardata.000webhostapp.com/api.php/vehicule?call=getData&maker=kia&model=rio%20sedan&year=2010

For every Kia Rio Sedan made in 2010.
```

* Specific columns result :
```- getMakers : https://cardata.000webhostapp.com/api.php/vehicule?call=getMakers&model=rio%20sedan

For every maker with a model car named 'rio sedan'

- getModels : https://cardata.000webhostapp.com/api.php/vehicule?call=getModels&maker=kia&year=2011

For every model whose maker is 'kia' produced in '2011'

- getTrim 
- getYear
```

### INFO
- Built this API for self-purpose and thought of sharing it here.
- Feel free to contribute.
- You can check the vehicule-database that the service is calling here : https://github.com/WiildchiilD/Vehicule-data-DB
- Give our a blog a check : http://www.themeleger.com/
- Tag-it is available here : https://github.com/cleishm/tag-it
