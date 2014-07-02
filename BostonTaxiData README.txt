README

Boston Taxi Data: March 2013 - May 2014, 10pm to 3am

Data is in CSV files by month
File title format is MMYY_[start/end], where MM is month, YY is year, and [start/end] is start for trip start locations and end for trip end locations


For each month there is a file for pickups and a file for drop offs. The TID field (trip ID) allows pick up and drop off to be linked
IMPORTANT: These locations have been filtered to exclude residential areas in order to protect individual privacy.
	The data are limited to the commercial areas and corridors designated by the City of Boston
	A given trip ID may only show up in either the start or end table if its corresponding record was in an excluded residential area

Field definitions:

TID: Trip ID - unique identifier for a trip, key linking start and end tables. A trip ID may not show up in both tables if a start or end has been excluded
[start/end]_gps_: start or end longitude
[start/end]_gps_1: start or end latitude
[start/end]_date: trip start or end date
time_: start or end time
