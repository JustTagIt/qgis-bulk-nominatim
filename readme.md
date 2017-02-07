# Bulk Nominatim Plugin

The ***Bulk Nominatim QGIS Plugin*** interfaces with an OpenStreetMap nominatim service to provide geocoding of addresses and reverse geocoding of coordinates. This plugin is only recommended to be used with personal nominatim servers because OpenStreetMap does not permit bulk nominatim requests.

## Installation
The plugin can be installed by downloading `bulknominatim.zip`, unzipping it and then moving the `bulknominatim` folder to `C:\Users\<Your User Name>\.qgis2\python\plugins` on Windows 7. Now launch QGIS and select ***Plugins->Manage and Install Plugins...*** from the menu. Click on the ***Installed*** tab on the left and make sure the check box next to ***Bulk Nominatim GeoCoding*** is checked. Click the ***Close*** button and you are ready to start address geocoding.

<div style="text-align:center"><img src="doc/install.jpg" alt="Installing Plugin"></div>


## Bulk Nominatim Tools

The plugin can be accessed from the `Plugins->Nominatim GeoCoding` menu or from the two tool bar icons.

<div style="text-align:center"><img src="doc/menu.jpg" alt="Nominatim GeoCoding"></div>

The menu items are:

* <img src="images/icon.png" alt="Bulk GeoCoding"> ***Bulk GeoCoding*** - Main tool for bulk geocoding of addresses to coordinates and reverse geocoding of coordinates to addresses.
* <img src="images/reverse.png" alt="Reverse Point GeoCoding"> ***Reverse Point GeoCoding*** - This tool allows the user to click on the map to determine the closest address or feature.
* <img src="images/settings.png" alt="Settings"> ***Settings*** - Configuration for the **Nominatim Service URL** as well as other settings.
* <img src="images/help.png" alt="Help"> ***Help*** - Displays help information for the tools.

Both ***Bulk GeoCoding*** and ***Reverse Point GeoCoding*** are also installed on the tool bar for quick access.

<div style="text-align:center"><img src="doc/toolbar.jpg" alt="Toolbar"></div>

### Bulk GeoCoding

Selecting this tool provides 3 different methods of geocoding. All three return a new vector layer.

* ***Geocode CSV File*** - Input is a CSV file that is delimited as either separate address fields or a single field that contains the address string. From the ***Browse*** button select a CSV file that contains the addresses to geocode. The plugin will attempt to find matches for the individual address fields *Street Number*, *Street Name*, *City*, *County*, *State*, *Country*, and *Postal Code*. The address fields can also be manually selected. If one of the fields contains the entire address select it from ***Full Address Field***. This overrides all the other field selections.
* ***Geocode Addresses*** - This is a text area where you can paste in addresses - one per line. The addresses are address strings and not individual fields.
* ***Reverse Geocode*** - Input is a points layer and it attempts to find the closest address for each point. For remote locations the closest feature may be an administrative boundary.

Across the top are three tabs representing these three geocoding tools. The lower part of the dialog box has common functionality for the three tools and are:

* ***Output Layer Name*** - This is the name of the vector layer that will be created in QGIS. Note that this is a memory vector layer and not a file layer. If you want to retain the results you will need to save the layer.
* ***Maximum Results*** - For each address multiple results can be returned. (Not applicable for ***Reverse Geocode***.)
* ***Label Geocoded Points*** - Automatically show the labels in QGIS for the geocoded point.
* ***Included Detailed Address Results*** - Returns an enhanced table of address details.
* ***Results*** - Shows the results of the geocoding and any addresses that failed.

Clicking on the ***OK*** button causes the plugin to start geocoding.

### Reverse Point GeoCoding
Clicking on this tool allows the user to be able to click on the map and return the closet feature/address in a dockable window. Note that the closes feature may be an administrative boundary or another feature that is not that close to the point clicked on. If the nominatim service is using the latest software, the actual polygon or point of the located feature will be displayed.

## Settings
In ***Settings*** the user can select the Nominatim Service URL endpoint, the maximum number of addresses to geocode and for reverse geocoding the level of detail where 0 represents the country and 18 the address number. Here is the dialog window.

<div style="text-align:center"><img src="doc/settings.jpg" alt="Settings"></div>

Please note that this plugin is designed to use commercial or personal Nominatim services. The OpenStreetMap URL displayed here is not for bulk use as it violates their policy and will result in the user being blocked from their site for a period of time.