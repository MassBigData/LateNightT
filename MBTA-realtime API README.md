Introducing: The new MBTA-realtime API
======================================

The new MBTA-realtime v2 API integrates predictions and alerts together for MBTA subway, commuter rail, and bus. The API supports new formats, calls and fields to make it easier than ever to develop a wide variety of applications using MBTA data.

As of August 5th 2014 The new API is now in production. New documentation and access instructions are available at [http://realtime.mbta.com].

The data challenge started before development was complete, so we set up special instance running test data. That is still available, and instructions for accessing it are in the "original MBTA-realtime docs" directory. However now that the API is in production there isn’t a real advantage in using the preview server. 

New Formats
-----------
The new MBTA-realtime API supports JSON-P, to make it easier to write web apps that access the API directly. JSON and XML continue to be supported. 

GTFS-realtime files now include prediction, location and alert information for MBTA subway, commuter rail and bus service (Green Line predictions are not yet available). 

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

Use *include_access_alerts* and *include_service_alerts* to specify whether you want alerts relating to accessibility (like elevator / escalator outages), alerts related to service (like delays), or both. 

Sample Calls 
------------
All the parameters and fields are spelled out in the documentation, but if you just want to try some calls and see what response you get, you can try the ones below. Remember that this is test data. Do not publish this to users. 

New Fields in Existing Alert Calls
--------------------------------
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

You can use a parent_stop for a stop parameter. You can request predictions for South Station parent stop ID ìplace-sstatî and get predictions for all subway, bus, and commuter rail departures from South Station with one call. 

Go to [http://realtime.mbta.com] to learn more. 
--------------
