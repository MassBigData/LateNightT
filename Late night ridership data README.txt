MBTA LATE NIGHT DATA

Data is number of transactions recorded by MBTA fare gates, buses, and light rail vehicles
Only includes transactions after 10pm on Fridays and Saturdays from March 1 2013 to June 14 2014
Transactions grouped by date, route or line, and 15-minute window.

Field definitions

scheduledate: service date, which includes hours after midnight (e.g. 1am on June 14 has a service date of June 13)
latenightroute: 0 = no late night service scheduled, 1 = late night service scheduled.
	This only indicates whether a route currently has late night service, not whether it had late night on that particular day
	Intended to facilitate comparisons for routes whose hours were extended
	Some routes will still have transactions after 1am even though they do not have extended hours, this is because their last trip is around 1am
line: indicates rapid transit line (Red, Blue, Orange, Green, Silver) or bus
routestation: indicates the station for rapid transit services and the route for bus services
trxdow: day of week, 5 = Friday 6 = Satruday
trxhour: hour, 22 (10pm) - 27 (3am)
trx15min: 15-min period, 0= :00-:14, 3= :045-:59
transactions: total transactions
