Important Note to Reader
-----------------------
This folder contains the original draft documentation, published for the data challenge along with a preview of the new API. The new API v2 is now in production, and improved documentation is available. It is recommended that you visit [http://realtime.mbta.com] and access the new documentation there. The “preview” copy of the API is still running, and the instructions below will still work. 

Introducing: The new MBTA-realtime API
======================================
The new MBTA-realtime v2 API integrates predictions and alerts together for MBTA subway, commuter rail, and bus. The API supports new formats, calls and fields to make it easier than ever to develop a wide variety of applications using MBTA data.

A preview of the new MBTA-realtime API *using test data* launched June 24, and comprehensive documentation is available. This document summarizes the differences between the new v2 API and the existing v1 API. We will also be collecting feedback, and may make adjustments to the API based on the feedback we collect. The new v2 API will be available in production before the end of July. 

Accessing the API During the Contest
------------------------------------
We've made a special instance of the API available for the contest. Remember that this API is publishing *test data.* 
IP address: 54.81.189.97
API key: wX9NwuHnZU2ToO7GmGR9uw
Sample: [http://54.81.189.97/developer/api/v2/servertime?api_key=wX9NwuHnZU2ToO7GmGR9uw&format=json]

Use this API key for all contest calls. If you want to get ready to launch an app in production, make sure you get an API key of your own at [http://realtime.mbta.com]

New Formats
-----------
The new MBTA-realtime API supports JSON-P, to make it easier to write web apps that access the API directly. JSON and XML continue to be supported. 

GTFS-realtime files will now include prediction, location and alert information for MBTA subway, commuter rail and bus service (Green Line predictions are not yet available). 

New API Calls
-------------
The API supports five new calls.

*predictionsbyroute,* *predictionsbytrip* and *predictionsbystop* give you both predictions for all service on a route, or a particular trip, or at a stop, and vehicle locations for the vehicles being predicted.

*vehiclesbyroute* and *vehiclesbystop* give vehicle locations only for all service on a route or for a specific trip. 

The data returned is organized the same way for both calls, and is much like the existing ìscheduleî calls: by mode, then route, then direction, then trip, then stop. IDs and text descriptions are given in each case. 

The prediction data includes scheduled arrival and departure time, predicted actual time, and predicted number of seconds away from right now. The vehicle location data includes latitude, longitude, bearing (if known), speed (if known), and a timestamp. 

Finally, if there are alerts that affect the service, the IDís and headers of those alerts are included in the prediction call. 

New Parameters for Existing Calls
---------------------------------
Use the *format* parameter to specify XML, JSON, or JSON-P. 

Use *include_access* and *include_service* to specify whether you want alerts relating to accessibility (like elevator / escalator outages), alerts related to service (like delays), or both. 

Sample Calls 
------------
All the parameters and fields are spelled out in the documentation, but if you just want to try some calls and see what response you get, you can try the ones below. Remember that this is test data. Do not publish this to users. 

[http://54.81.189.97/developer/api/v2/servertime?api_key=wX9NwuHnZU2ToO7GmGR9uw&format=json]
[http://54.81.189.97/developer/api/v2/routes?api_key=wX9NwuHnZU2ToO7GmGR9uw&format=json]
[http://54.81.189.97/developer/api/v2/routesbystop?api_key=wX9NwuHnZU2ToO7GmGR9uw&stop=70065&format=json]
[http://54.81.189.97/developer/api/v2/stopsbyroute?api_key=wX9NwuHnZU2ToO7GmGR9uw&route=931_&format=json]
[http://54.81.189.97/developer/api/v2/stopsbylocation?api_key=wX9NwuHnZU2ToO7GmGR9uw&lat=42.352913&lon=-71.064648&format=json]
[http://54.81.189.97/developer/api/v2/schedulebystop?api_key=wX9NwuHnZU2ToO7GmGR9uw&stop=Back%20Bay&route=CR-Providence&direction=0&format=json]
[http://54.81.189.97/developer/api/v2/schedulebyroute?api_key=wX9NwuHnZU2ToO7GmGR9uw&route=CR-Providence&direction=0&format=json]
[http://54.81.189.97/developer/api/v2/schedulebytrip?api_key=wX9NwuHnZU2ToO7GmGR9uw&trip=CR-Providence-CR-Weekday-Providence-Dec13-813&format=json]
[http://54.81.189.97/developer/api/v2/alerts?api_key=wX9NwuHnZU2ToO7GmGR9uw&include_access_alerts=true&include_service_alerts=true&format=json]
[http://54.81.189.97/developer/api/v2/alertsbyroute?api_key=wX9NwuHnZU2ToO7GmGR9uw&route=931_&include_access_alerts=true&include_service_alerts=true&format=json]
[http://54.81.189.97/developer/api/v2/alertsbystop?api_key=wX9NwuHnZU2ToO7GmGR9uw&stop=Porter%20Square&include_access_alerts=true&include_service_alerts=true&format=json]
[http://54.81.189.97/developer/api/v2/alertbyid?api_key=wX9NwuHnZU2ToO7GmGR9uw&include_access_alerts=true&include_service_alerts=true&id=33274&format=json]
[http://54.81.189.97/developer/api/v2/alertbyid?api_key=wX9NwuHnZU2ToO7GmGR9uw&include_access_alerts=true&include_service_alerts=true&id=33274&format=json]
[http://54.81.189.97/developer/api/v2/alertheaders?api_key=wX9NwuHnZU2ToO7GmGR9uw&include_access_alerts=true&include_service_alerts=true&format=json]
[http://54.81.189.97/developer/api/v2/alertheadersbyroute?api_key=wX9NwuHnZU2ToO7GmGR9uw&route=931_&include_access_alerts=true&include_service_alerts=true&format=json]
[http://54.81.189.97/developer/api/v2/alertheadersbystop?api_key=wX9NwuHnZU2ToO7GmGR9uw&stop=Porter%20Square&include_access_alerts=true&include_service_alerts=true&format=json]
[http://54.81.189.97/developer/api/v2/predictionsbyroute?api_key=wX9NwuHnZU2ToO7GmGR9uw&route=CR-Providence&format=json]
[http://54.81.189.97/developer/api/v2/predictionsbystop?api_key=wX9NwuHnZU2ToO7GmGR9uw&stop=Providence&format=json]
[http://54.81.189.97/developer/api/v2/predictionsbytrip?api_key=wX9NwuHnZU2ToO7GmGR9uw&trip=CR-Providence-CR-Weekday-Providence-Dec13-913&format=json]
[http://54.81.189.97/developer/api/v2/vehiclesbyroute?api_key=wX9NwuHnZU2ToO7GmGR9uw&route=CR-Providence&format=json]
[http://54.81.189.97/developer/api/v2/vehiclesbytrip?api_key=wX9NwuHnZU2ToO7GmGR9uw&trip=CR-Providence-CR-Weekday-Providence-Dec13-818&format=json]

And here is GTFS-realtime: 
[http://developer.mbta.com/lib/GTRTFS/Alerts/Alerts.pb]
[http://developer.mbta.com/lib/GTRTFS/Alerts/TripUpdates.pb]
[http://developer.mbta.com/lib/GTRTFS/Alerts/VehiclePositions.pb]

New Fields in Existing Alert Calls
----------------------------
The following is a list of new fields in the alerts calls: 
<table border="1" cellspacing="0" cellpadding="0">
    <tbody>
        <tr>
            <td width="134" valign="top">
                <p>
                    Field
                </p>
            </td>
            <td width="149" valign="top">
                <p>
                    Description
                </p>
            </td>
            <td width="400" valign="top">
                <p>
                    Sample Values
                </p>
            </td>
        </tr>
        <tr>
            <td width="134" valign="top">
                <p>
                    service_effect_text
                </p>
            </td>
            <td width="149" valign="top">
                <p>
                    Very short text summary of alert
                </p>
            </td>
            <td width="400" valign="top">
                <ul>
                    <li>
                        Red Line shuttle
                    </li>
                    <li>
                        Minor route 1 delay
                    </li>
                    <li>
                        South Station closure
                    </li>
                    <li>
                        Bus detour
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td width="134" valign="top">
                <p>
                    short_header_text
                </p>
            </td>
            <td width="149" valign="top">
                <p>
                    Like header_text but shortened to 140 characters
                </p>
            </td>
            <td width="400" valign="top">
                <p>
                    ∑ Buses replacing Green Line C service btn Coolidge Cnr &amp; Cleveland Cir fm Sat Jun 21 through Sun Jun 22. Connect to D branch at
                    Cleveland Cir
                </p>
            </td>
        </tr>
        <tr>
            <td width="134" valign="top">
                <p>
                    Timeframe_text
                </p>
            </td>
            <td width="149" valign="top">
                <p>
                    Text description of when an upcoming alert is effective
                </p>
            </td>
            <td width="400" valign="top">
                <ul>
                    <li>
                        Monday
                    </li>
                    <li>
                        this weekend
                    </li>
                    <li>
                        later today
                    </li>
                    <li>
                        starting August 12
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td width="134" valign="top">
                <p>
                    Recurrencence_text
                </p>
            </td>
            <td width="149" valign="top">
                <p>
                    Text description of how a repeating alert repeats
                </p>
            </td>
            <td width="400" valign="top">
                <ul>
                    <li>
                        daily
                    </li>
                    <li>
                        weekends
                    </li>
                    <li>
                        Mondays
                    </li>
                    <li>
                        Sunday-Thursday
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td width="134" valign="top">
                <p>
                    banner_text
                </p>
            </td>
            <td width="149" valign="top">
                <p>
                    Indicates that an alert should be front and center to all users, with the text to use.
                </p>
            </td>
            <td width="400" valign="top">
                <p>
                    ∑ Shuttle buses replacing Red Line service between Harvard Station and Andrew Station. Seek alternate routes if possible.
                </p>
            </td>
        </tr>
        <tr>
            <td width="134" valign="top">
                <p>
                    Alert_lifecycle
                </p>
            </td>
            <td width="149" valign="top">
                <p>
                    Flag indicating whether an alert is currently in effect and whether it's new.
                </p>
            </td>
            <td width="400" valign="top">
                <ul>
                    <li>
                        <strong>New</strong>
                        (Happening now, relatively new information)
                    </li>
                    <li>
                        <strong>Upcoming</strong>
                        (Happens in future)
                    </li>
                    <li>
                        <strong>Ongoing</strong>
                        ("Old news," happening now and has been for a while)
                    </li>
                    <li>
                        <strong>Upcoming-Ongoing</strong>
                        (Both Upcoming and Ongoing, i.e. if today is Monday and we are shuttling a service every weekend and have been for a long time)
                    </li>
                </ul>
            </td>
        </tr>
        <tr>
            <td width="134" valign="top">
                <p>
                    route_hide
                </p>
            </td>
            <td width="149" valign="top">
                <p>
                    In some circumstances route shouldn't be listed (see below)
                </p>
            </td>
            <td width="400" valign="top">
                <ul>
                    <li>
                        true
                    </li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>
<p>

_Example of Route_hide: Route_hide is generally for what the MBTA calls ìhybridî routes, like route 62/76, which is a combination of route 62 and route 76 that runs on Saturdays. Route 62 and route 76 and route 62/76 are three separate routes in GTFS, but to a rider a route 62/76 trip is a trip on both route 62 and route 76. So if a detour affects route 62 and route 62/76 it isnít necessary to specify to the user that itís affecting route 62/76, thatís implicit as long as you specify that itís affecting route 62._
 
Other Changes
-------------
XML header changed to include data that is technically optional but which some parsers expect. 

No more empty strings ñ if a field isnít applicable itís not included. 

You can use a parent_stop for a stop parameter. In GTFS a stationís inbound platform, outbound platform, busway, etc. might be represented by different stop IDís that all share the same ìparent stop.î That means you can request predictions for South Station parent stop ID ìplace-sstatî and get predictions for all subway, bus, and commuter rail departures from South Station with one call. 

Sample Calls
------------



Sample Output
-------------
*predictionsbystop* (stop_id=93):
```xml
<predictions xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" stop_id="93" stop_name="Massachusetts Ave @ Newbury St">  
<mode route_type="3" mode_name="Bus">  
<route route_id="01" route_name="1">  
<direction direction_id="0" direction_name="Outbound">  
<trip trip_id="22625711" trip_name="4:51 pm from Dudley Station to Massachusetts Ave @ Holyoke St" trip_headsign="Harvard Station via Mass. Ave." sch_arr_dt="1403125920" sch_dep_dt="1403125920" pre_dt="1403126580" pre_away="328">  
<vehicle vehicle_id="y2148" vehicle_lat="42.3429679870605" vehicle_lon="-71.0852813720703" vehicle_timestamp="1403126210"/>  
</trip>  
<trip trip_id="22625657" trip_name="4:59 pm from Dudley Station to Massachusetts Ave @ Holyoke St" trip_headsign="Harvard Station via Mass. Ave." sch_arr_dt="1403126460" sch_dep_dt="1403126460" pre_dt="1403127000" pre_away="748">  
<vehicle vehicle_id="y2137" vehicle_lat="42.3372535705566" vehicle_lon="-71.0779190063477" vehicle_timestamp="1403126237"/>  
</trip>  
<trip trip_id="22625693" trip_name="5:07 pm from Dudley Station to Massachusetts Ave @ Holyoke St" trip_headsign="Harvard Station via Mass. Ave." sch_arr_dt="1403126940" sch_dep_dt="1403126940" pre_dt="1403127060" pre_away="808">  
<vehicle vehicle_id="y2159" vehicle_lat="42.3348579406738" vehicle_lon="-71.0748062133789" vehicle_timestamp="1403126197"/>  
</trip>  
</direction>  
</route>  
<route route_id="701" route_name="CT1">  
<direction direction_id="0" direction_name="Outbound">  
<trip trip_id="22494611" trip_name="4:55 pm from 88 E Newton St to Magazine St @ Green St" trip_headsign="Central Square (Limited Stops)" sch_arr_dt="1403125860" sch_dep_dt="1403125860" pre_dt="1403126280" pre_away="28">  
<vehicle vehicle_id="y0447" vehicle_lat="42.3456230163574" vehicle_lon="-71.0869064331055" vehicle_timestamp="1403126186"/>  
</trip>  
</direction>  
</route>  
</mode>  
</predictions>
```

*alerts* (one alert, effect_periods and services have been abridged; alert is fictional)
```xml
<alert alert_id="123456">  
<effect_name>Shuttle</effect_name>  
<effect>DETOUR</effect>  
<cause_name>construction</cause_name>  
<cause>CONSTRUCTION</cause>  
<header_text>From June 22 through August 31: Shuttle buses replacing Orange Line service between Oak Grove and North Station on weekends for the signal enhancement project. </header_text> 
<short_header_text>fm Jun 22 thru Aug 31: Shuttle buses replacing Orange Line service btn Oak Grove and North Sta on weekends for the signal enhancement project </short_header_text>  
<description_text>Affected stops: Oak Grove Station, Malden Center Station, Wellington Station, Sullivan Station, Community College Station, North Station. All shuttle buses will be accessible to persons with disabilities.  </description_text>
<severity>Severe</severity>  
<created_dt>1403124331</created_dt>  
<last_modified_dt>1403124331</last_modified_dt>  
<service_effect_text>Orange Line shuttle</service_effect_text>  
<timeframe_text>starting Sunday</service_effect_text>  
<alert_lifecycle>Upcoming</alert_lifecycle>  
<recurrence_text>weekends</recurrence_text>  
<effect_periods>  
<effect_period effect_start="1403425800" effect_end="1403505000"/>  
<effect_period effect_start="1403944200" effect_end="1404023400"/>  
<!--- This example is abridged for readability --->
</effect_periods>  
<affected_services>  
<services>  
<service route_type="1" mode_name="Subway" route_id="903_" route_name="Orange Line" stop_id="70026" stop_name="North Station - Inbound"/>  
<service route_type="1" mode_name="Subway" route_id="903_" route_name="Orange Line" stop_id="70027" stop_name="North Station - Outbound"/>  
<!--- This example is abridged for readability --->
</services>  
<elevators/>  
</affected_services>  
</alert>
```