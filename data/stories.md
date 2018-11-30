## first story: find an address
* Default Welcome Intent
	- utter_handle_welcome
* find.address{"city": "Nice", "accomodation":"hôtel Negresco"}
	- action_find_address
* find.restaurant{"city":"Nice"}
	- action_find_restaurant

## second story: discover a city and events in that city 
* Default Welcome Intent
	- utter_handle_welcome
* discover.city{"city": "Nice", "accomodation":"hôtel Negresco"}
	- action_discover_city
* find.event{"city":"Nice", "datetime":"today"}
	- action_find_event
* find.more
	- action_find_more
	- slots{"city":"Nice"}

## third story: find poi and get good suggestions
* Default Welcome Intent
	- utter_handle_welcome
* find.poi{"city": "Nice"}
	- action_find_poi
* find.alternative{"city":"Antibes", "datetime":"tomorrow"}
	- action_find_alternative
* leave.positive
	- utter_handle_leave_pos

## fourth story: find shopping and get bad suggestions
* Default Welcome Intent
	- utter_handle_welcome
* find.shopping{"city": "Marseille"}
	- action_find_poi
* find.alternative{"city":"Marseille", "datetime":"today"}
	- action_find_alternative
* leave.negative
	- utter_handle_leave_neg

## fith story: ask about the weather
* Default Welcome Intent
	- utter_handle_welcome
* weather{"city": "Marseille"}
	- action_weather
* find.activity{"city":"Marseille"}
	- action_find_activity
* leave.postive
	- utter_handle_leave_pos

