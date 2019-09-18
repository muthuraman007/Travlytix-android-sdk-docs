<link href="https://storage.googleapis.com/travlytix-web-sdk-doc/styles.css" rel="stylesheet"></link>

# Travlytix Android SDK vX.X.X - Integration Documentation


This documentation guides you on how to integrate the travlytix event to your app code base with some simple code examples. 

List of available travlytix events are:

* Search Event

* MultiCity Search Event

* Search Results Event

* Selected Flight Event

* Passenger Event

* Baggage Event

* Meals Event

* Seats Event

* Insurance Event

* Ancillaries Event

* Payment Event

* Confirm Event

## **Search Event**

Send user's flight search details with this event.

## Class
| Name | Type  | Description |
| :--- | :---  | :--- | 
| Search | Class | Search |


##  Constants (in Search)
| Name | Type  | Description |
| :--- | :---  | :--- | 
| RETURN | String  | Use this to indicate return or round trip journey type. |
| ONE_WAY | String | Use this to indicate one way journey type. |



## Methods (in Search)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setOrigin(String) | yes | IATA code of origin airport i.e. `KUL` |
| setDestination(String) | yes | IATA code of destination airport i.e. `SIN`  |
| setDepartureDate(String) | yes | Departure Date, must be in `YYYY-MM-DD` format, i.e. `2019-01-15` |
| setReturnDate(String) | no | Return Date, must be in  `YYYY-MM-DD` format, i.e. `2019-01-20`|
| setTripType(String) | yes | Must be either `one_way_trip` or `return_trip`  |
| setNoOfAdults(Integer) | yes | Number of adult passengers, Must be more than or equal to 1 |
| setNoOfChildren(Integer) | no | Number of child passengers, Must be more than or equal to 0 |
| setNoOfInfants(Integer) | no | Number of infant passengers, Must be more than or equal to 0 |
| setPromoCode(String) | no | Promotion code used for flight search |
| setCabinClass(String) | no | Preferred Cabin class  |


## Example

```
Search search = new Search();

search.setOrigin("KUL");
search.setDestination("SIN");
search.setDepartureDate("2019-01-15");
search.setReturnDate("2019-01-20");
search.setTripType(Search.RETURN);
search.setNoOfAdults(1);
search.setNoOfChildren(0);
search.setNoOfInfants(0);
search.setPromoCode("XXX");
search.setCabinClass("XX");

Travlytix.Flight.Search(search);
Travlytix.send();

```

### **Note:** 
After you create the each request, you should need to call the `Travlytix.send()` method to send details to travlytix api. It is applicable to all travlytix events.

---

## **MultiCity Search Event**

Send user's multicity flight search details with this event.

## Class
| Name | Type  | Description |
| :--- | :---  | :--- | 
| MultiCitySearch | Class | MultiCitySearch |
| RouteItem | Class | Route details |

## Fields (in MultiCitySearch)

| Name | Type | Required | Description |
| :---| :--- | :--- | :--- |
| routeItemList | List\<RouteItem> | yes | List of route details |


## Methods (in MultiCitySearch)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setNoOfAdults(Integer) | yes | Number of adult passengers, Must be more than or equal to 1 |
| setNoOfChildren(Integer) | no | Number of child passengers, Must be more than or equal to 0 |
| setNoOfInfants(Integer) | no | Number of infant passengers, Must be more than or equal to 0 |
| setPromoCode(String) | no | Promotion code used for flight search |
| setCabinClass(String) | no | Preferred Cabin class  |


## Methods (in RouteItem)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setOrigin(String) | yes | IATA code of origin airport i.e. `KUL` |
| setDestination(String) | yes | IATA code of destination airport i.e. `SIN` |
| setDate(String) | yes | Travel date, must be in `YYYY-MM-DD` format, i.e. `2019-01-15` |

## Example
```
        MultiCitySearch multiCitySearch = new MultiCitySearch();

        RouteItem routeItem1 = new RouteItem();
        routeItem1.setOrigin("KUL");
        routeItem1.setDestination("SIN");
        routeItem1.setDate("2019-01-15");

        RouteItem routeItem2 = new RouteItem();
        routeItem2.setOrigin("SIN");
        routeItem2.setDestination("DMK");
        routeItem2.setDate("2019-01-20");

        RouteItem routeItem3 = new RouteItem();
        routeItem3.setOrigin("DMK");
        routeItem3.setDestination("DPS");
        routeItem3.setDate("2019-01-25");

        multiCitySearch.routeItemList.add(routeItem1);
        multiCitySearch.routeItemList.add(routeItem2);
        multiCitySearch.routeItemList.add(routeItem3);

        multiCitySearch.setNoOfAdults(1);
        multiCitySearch.setNoOfChildren(0);
        multiCitySearch.setNoOfInfants(0);
        multiCitySearch.setPromoCode("OFF01");
        multiCitySearch.setCabinClass("E");


        Travlytix.Flight.MultiCitySearch(multiCitySearch);
        Travlytix.send();
```
---

## **Search Results Event**

Send the available flight search results shown to user with this event.

## Class 
| Name | Type  | Description |
| :--- | :---  | :--- | 
| SearchResultItem | Class | Search result item |
| RouteItem | Class | Route details |
| ResultItem | Class | Result item |
| FlightItem | Class | Flight segment details |
| CabinItem | Class | Cabin details |


## Fields (in SearchResultItem)

| Name | Type | Required | Description |
| :---| :--- | :--- | :--- |
| routeItemList | List\<RouteItem> | yes | List of route details |
| resultItemList | List\<ResultItem> | no | List of result item |


## Methods (in SearchResultItem)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setHasResult(Boolean) | yes | Indicates flight result available or not. |



## Methods (in RouteItem)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setOrigin(String) | yes | IATA code of origin airport i.e. `KUL` |
| setDestination(String) | yes | IATA code of destination airport i.e. `SIN` |
| setDate(String) | yes | Travel date, must be in `YYYY-MM-DD` format, i.e. `2019-01-15` |


## Fields (in ResultItem)

| Name | Type | Required | Description |
| :---| :--- | :--- | :--- |
| flightItemList | List\<FlightItem> | yes | List of flight segment details. |
| cabinItemList | List\<CabinItem> | yes | list of cabin class and fare. |


## Methods (in ResultItem)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setTotalDuration(Integer) | no | Total flight duration in minutes |


## Methods (in FlightItem)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setNumber(String) | yes | Flight number i.e `123` |
| setOperatingAirline(String) | no | Operating airline code |
| setMarketingAirline(String) | no | Marketing airline code |
| setDepartureAirport(String) | yes | IATA code of departure airport i.e. `KUL` |
| setArrivalAirport(String) | yes | IATA code of arrival airport i.e. `SIN`|
| setDepartureDatetime(String) | yes | Departure date and time of flight segment, i.e. `2019-01-15T12:10:00` |
| setArrivalDatetime(String) | yes | Arrival date and time of flight segment i.e. `2019-01-20T12:10:00` |
| setDuration(Integer) | no | Flight segment duration in minutes |


## Methods (in CabinItem)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setType(String) | yes | Cabin type, i.e. `eco`, `bus` and etc |
| setBookingClass(String) | no | Booking class |
| setFareBasisCode(String) | no | Fare basis code |
| setFare(BigDecimal) | yes | Fare |
| setCurrency(String) | yes | ISO 4217 currency code |



## Example

```
// Departure Flight
SearchResultItem departSearchResultItem = new SearchResultItem();

departSearchResultItem.setHasResult(true);

RouteItem departRouteItem1 = new RouteItem();
departRouteItem1.setOrigin("KUL");
departRouteItem1.setDestination("SIN");
departRouteItem1.setDate("2019-01-15");
departSearchResultItem.routeItemList.add(departRouteItem1);


ResultItem departResultItem = new ResultItem();
departResultItem.setTotalDuration(60);

FlightItem departFlightItem1 = new FlightItem();
departFlightItem1.setNumber("123");
departFlightItem1.setOperatingAirline("XX");
departFlightItem1.setMarketingAirline("XX");
departFlightItem1.setDepartureAirport("KUL");
departFlightItem1.setArrivalAirport("SIN");
departFlightItem1.setDepartureDatetime("2019-01-15T06:10:00");
departFlightItem1.setArrivalDatetime("2019-01-15T07:10:00");
departFlightItem1.setDuration(60);


departResultItem.flightItemList.add(departFlightItem1);

CabinItem departCabinItem1 = new CabinItem();
departCabinItem1.setType("eco");
departCabinItem1.setBookingClass("F");
departCabinItem1.setFareBasisCode("FBCWE");
departCabinItem1.setFare(new BigDecimal("200.00"));
departCabinItem1.setCurrency("MYR");

departResultItem.cabinItemList.add(departCabinItem1);


departSearchResultItem.resultItemList.add(departResultItem);


//Return Flight
SearchResultItem returnSearchResultItem = new SearchResultItem();

returnSearchResultItem.setHasResult(true);

RouteItem returnRouteItem1 = new RouteItem();
returnRouteItem1.setOrigin("SIN");
returnRouteItem1.setDestination("KUL");
returnRouteItem1.setDate("2019-01-20");
returnSearchResultItem.routeItemList.add(returnRouteItem1);


ResultItem returnResultItem = new ResultItem();
returnResultItem.setTotalDuration(60);

FlightItem returnFlightItem1 = new FlightItem();
returnFlightItem1.setNumber("123");
returnFlightItem1.setOperatingAirline("XX");
returnFlightItem1.setMarketingAirline("XX");
returnFlightItem1.setDepartureAirport("SIN");
returnFlightItem1.setArrivalAirport("KUL");
returnFlightItem1.setDepartureDatetime("2019-01-20T13:00:00");
returnFlightItem1.setArrivalDatetime("2019-01-20T14:00:00");
returnFlightItem1.setDuration(60);


returnResultItem.flightItemList.add(returnFlightItem1);

CabinItem returnCabinItem1 = new CabinItem();
returnCabinItem1.setType("bus");
returnCabinItem1.setBookingClass("F");
returnCabinItem1.setFareBasisCode("FBCWB");
returnCabinItem1.setFare(new BigDecimal("330.00"));
returnCabinItem1.setCurrency("MYR");

returnResultItem.cabinItemList.add(returnCabinItem1);


returnSearchResultItem.resultItemList.add(returnResultItem);


SearchResults searchResults = new SearchResults();

searchResults.searchResultItemList.add(departSearchResultItem);

searchResults.searchResultItemList.add(returnSearchResultItem);

Travlytix.Flight.SearchResults(searchResults);
Travlytix.send();
```
---

## **Selected Flight Event**

Send user selected flight details with this event.


## Class

| Name | Type  | Description |
| :--- | :---  | :--- | 
| SelectedFlights | Class | Selected flights  |
| SelectionItem | Class | Selection item |
| RouteItem | Class | Route details |
| FlightItem | Class | Flight details |
| CabinItem | Clas | Cabin details |


## Fields (in SelectedFlights)

| Name | Type | Required | Description |
| :---| :--- | :--- | :--- |
| selectionItemList | List\<SelectionItem> | yes | List of selection items. |


## Fields (in SelectionItem)

| Name | Type | Required | Description |
| :---| :--- | :--- | :--- |
| routeItemList | List\<RouteItem> | yes | List of route details. |
| flightItemList | List\<FlightItem> | yes | List of selected flight segment details. |


## Methods (in SelectionItem)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setCabinItem(CabinItem) | yes | Selected cabin details |
| setTotalDuration(Integer) | no | Total travel duration in minutes |


## Methods (in RouteItem)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setOrigin(String) | yes | IATA code of origin airport i.e. `KUL` |
| setDestination(String) | yes | IATA code of destination airport i.e. `SIN` |
| setDate(String) | yes | Travel date, must be in `YYYY-MM-DD` format i.e. `2019-01-15` |


## Methods (in FlightItem)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setNumber(String) | yes | Flight number i.e. `123` |
| setOperatingAirline(String) | no | Operating airline code |
| setMarketingAirline(String) | no | Marketing airline code |
| setDepartureAirport(String) | yes | IATA code of departure airport i.e. `KUL` |
| setArrivalAirport(String) | yes | IATA code of arrival airport i.e. `SIN` |
| setDepartureDatetime(String) | yes | Departure date and time of flight segment, i.e. `2019-01-15T12:10:00`|
| setArrivalDatetime(String) | yes | Arrival date and time of flight segment, i.e. `2019-01-20T12:10:00` |
| setDuration(Integer) | no | Flight segment duration in minutes |


## Methods (in CabinItem)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setType(String) | yes | Cabin type, i.e. `eco`, `bus` and etc |
| setBookingClass(String) | no | Booking class |
| setFareBasisCode(String) | no | Fare basis code |
| setFare(BigDecimal) | yes | Fare |
| setCurrency(String) | yes | ISO 4217 currency code |


## Example

```
SelectedFlights selectedFlights = new SelectedFlights();

SelectionItem departSelectionItem = new SelectionItem();
departSelectionItem.setTotalDuration(60);


RouteItem departRouteItem1 = new RouteItem();
departRouteItem1.setOrigin("KUL");
departRouteItem1.setDestination("SIN");
departRouteItem1.setDate("2019-01-15");

departSelectionItem.routeItemList.add(departRouteItem1);


FlightItem departFlightItem1 = new FlightItem();
departFlightItem1.setNumber("123");
departFlightItem1.setOperatingAirline("XX");
departFlightItem1.setMarketingAirline("XX");
departFlightItem1.setDepartureAirport("KUL");
departFlightItem1.setArrivalAirport("SIN");
departFlightItem1.setDepartureDatetime("2019-01-15T06:10:00");
departFlightItem1.setArrivalDatetime("2019-01-15T07:10:00");
departFlightItem1.setDuration(60);


departSelectionItem.flightItemList.add(departFlightItem1);

CabinItem departCabinItem1 = new CabinItem();
departCabinItem1.setType("eco");
departCabinItem1.setBookingClass("F");
departCabinItem1.setFareBasisCode("FBCWE");
departCabinItem1.setFare(new BigDecimal("200.00"));
departCabinItem1.setCurrency("MYR");

departSelectionItem.setCabinItem(departCabinItem1);


SelectionItem returnSelectionItem = new SelectionItem();
returnSelectionItem.setTotalDuration(60);

RouteItem returnRouteItem1 = new RouteItem();
returnRouteItem1.setOrigin("SIN");
returnRouteItem1.setDestination("KUL");
returnRouteItem1.setDate("2019-01-20");

returnSelectionItem.routeItemList.add(returnRouteItem1);


FlightItem returnFlightItem1 = new FlightItem();
returnFlightItem1.setNumber("123");
returnFlightItem1.setOperatingAirline("XX");
returnFlightItem1.setMarketingAirline("XX");
returnFlightItem1.setDepartureAirport("SIN");
returnFlightItem1.setArrivalAirport("KUL");
returnFlightItem1.setDepartureDatetime("2019-01-20T13:00:00");
returnFlightItem1.setArrivalDatetime("2019-01-20T14:00:00");
returnFlightItem1.setDuration(60);

returnSelectionItem.flightItemList.add(returnFlightItem1);


CabinItem returnCabinItem1 = new CabinItem();
returnCabinItem1.setType("bus");
returnCabinItem1.setBookingClass("F");
returnCabinItem1.setFareBasisCode("FBCWB");
returnCabinItem1.setFare(new BigDecimal("330.00"));
returnCabinItem1.setCurrency("MYR");


returnSelectionItem.setCabinItem(returnCabinItem1);

selectedFlights.selectionItemList.add(departSelectionItem);
selectedFlights.selectionItemList.add(returnSelectionItem);

Travlytix.Flight.Select(selectedFlights);
Travlytix.send();

```

---


## **Passenger Event**

Send user entered passenger details with this event.

## Class
| Name | Type  | Description |
| :--- | :---  | :--- | 
| Passengers | Class | Passengers Root |
| PassengerItem | Class | Passenger Details |
| Passport | Class | Passport details |
| FrequentFlyer | Class | FrequentFlyer details |



## Constants (in Passengers)

| Name | Type  | Description |
| :--- | :---  | :--- | 
| ADULT | String | Use this to indicate Adult passengers |
| CHILD | String | Use this to indicate Child passengers |
| INFANT | String | Use this to indicate Infant passenger |
| MALE | String | Use this to indicate Male gender |
| FEMALE | String | Use this to indicate Female gender |



## Fields (in Passengers)

| Name | Type | Required | Description |
| :---| :--- | :--- | :--- |
| passengerItemList | List\<PassengerItem> |  yes | List of passengers |



## Methods (in PassengerItem)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setPaxType(String) | yes | Passenger type, must be either `adult`,`child` or `infant` |
| setTitle(String) | no | Title prefix of name, i.e. `Mr.`, `Mrs.`, `Miss` and etc |
| setFirstName(String) | yes | Given name or First name of passenger |
| setLastName(String) | yes | Surname or Last name of passenger |
| setBirthDate(String) | no | Date of birth, must be in `YYYY-MM-DD` format, i.e. `1995-07-29` |
| setGender(String) | no | Gender, Must be either `male` or `female` |
| setPassport(Passport) | no | Passport Details |
| setNationality(String) | no | Country ISO 3166 code, i.e. `MYS` for Malaysia |
| setFrequentFlyer(frequentFlyer) |no | Frequent Flyer Details |


## Methods (in Passport)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setNumber(String) | yes | Passport number |
| setIssueCountry(String) | no | Country ISO 3166 code, i.e. `MYS` for Malaysia |
| setExpiryDate(String) | no | Passport Expiry Date, must be in `YYYY-MM-DD` format, i.e. `2020-05-16` |


## Methods (in FrequentFlyer)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setId(String) | no | Membership ID of frequent flyer program |
| setName(String) | no | Name of frequent flyer program |


## Example

```
Passengers passengers = new Passengers();

PassengerItem  = new PassengerItem();

passengerItem1.setPaxType(PassengerItem.ADULT);
passengerItem1.setTitle("Mr.");
passengerItem1.setFirstName("John");
passengerItem1.setLastName("Smith");
passengerItem1.setBirthDate("1990-08-05");
passengerItem1.setGender(PassengerItem.MALE);

Passport passport = new Passport();
passport.setNumber("Pass001");
passport.setIssueCountry("MYS");
passport.setExpiryDate("2020-10-05");
passengerItem1.setPassport(passport);

passengerItem1.setNationality("MYS");

FrequentFlyer frequentFlyer = new FrequentFlyer();
frequentFlyer.setId("XX0000");
frequentFlyer.setName("XX Air");
passengerItem1.setFrequentFlyer(frequentFlyer);

passengers.passengerItemList.add(passengerItem1);

//... Continue add for other passengers

Travlytix.Flight.Passengers(passengers);
Travlytix.send();
```

---


## **Baggage Event**

Send user selected baggage information with this event.

## Class
| Name | Type  | Description |
| :--- | :---  | :--- | 
| Baggage | Class | Baggage Root |
| BaggageItem | Class | Baggage details |


## Fields (in Baggage)

| Name | Type | Required | Description |
| :---| :--- | :--- | :--- |
| baggageItemList| List<BaggageItem> | yes | List of selected baggage details |



## Methods (in BaggageItem)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setType(String) | yes | Free or Extra |
| setWeight(Integer) | yes | Baggage weight in Kg |
| setPrice(BigDecimal) | no | Baggage price |
| setCurrency(String) | no | ISO 4217 currency code |
| setOrigin(String) | yes |  IATA code of origin airport, i.e. `KUL` |
| setDestination(String) | yes | IATA code of destination airport, i.e. `SIN` |
| setFirstName(String) | yes |  Given name or First name of passenger |
| setLastName(String) | yes |  Surname or Last name of passenger |

## Example

```
Baggage baggage = new Baggage();

BaggageItem baggageItem1 = new BaggageItem();

baggageItem1.setType("Extra");
baggageItem1.setWeight(5);
baggageItem1.setPrice(price);
baggageItem1.setCurrency("MYR");
baggageItem1.setOrigin("KUL");
baggageItem1.setDestination("SIN");
baggageItem1.setFirstName("John");
baggageItem1.setLastName("Smith");

baggage.baggageItemList.add(baggageItem1);

//... Continue add for other passengers and routes (like outbound, inbound)

Travlytix.Flight.Baggage(baggage);
Travlytix.send();

```

---



## **Meals Event**

Send user selected meal details with this event.

## Class
| Name | Type  | Description |
| :--- | :---  | :--- | 
| Meals | Class | Meals root |
| MealItem | Class | Meal details |



## Fields (in Meals)

| Name | Type | Required | Description |
| :---| :--- | :--- | :--- |
| mealItemList| List\<MealItem> | yes | List of selected meal details |




## Methods (in MealItem)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setName(String) | yes | Meal name |
| setPrice(BigDecimal) | no | Meal price |
| setCurrency(String) | no |  ISO 4217 currency code |
| setOrigin(String) | yes |  IATA code of origin airport, i.e. `KUL` |
| setDestination(String) | yes | IATA code of destination airport, i.e. `SIN` |
| setFirstName(String) | yes |  Given name or First name of passenger |
| setLastName(String) | yes |  Surname or Last name of passenger |


## Example

```
Meals meals = new Meals();

MealItem mealItem1 = new MealItem();

mealItem1.setName("Veg rice");
mealItem1.setPrice(price);
mealItem1.setCurrency("MYR");
mealItem1.setOrigin("KUL");
mealItem1.setDestination("SIN");
mealItem1.setFirstName("John");
mealItem1.setLastName("Smith");

meals.mealItemList.add(mealItem1);

//.. Continue add for other passengers & routes 

Travlytix.Flight.Meals(meals);
Travlytix.send();

```

## **Seats Event**

Send user selected seat details with this event.

## Class
| Name | Type  | Description |
| :--- | :---  | :--- | 
| Seats | Class | Seats root|
| SeatItem | Class | Seat details |


## Fields (in Seats)
| Name | Type | Required | Description |
| :---| :--- | :--- | :--- |
| seatItemList | List\<SeatItem> | yes | List of selected seat details. |


## Methods (in SeatItem)
| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setType(String)  | yes | Seat type, i.e. `Flat bed`, `Extra Legroom` and etc  |
| setSeatNumber(String) | yes | Seat number, i.e. `13A` |
| setPrice(BigDecimal) | no | Seat price |
| setCurrency(String) | no | ISO 4217 currency code |
| setOrigin(String) | yes | IATA code of origin airport, i.e. `KUL` |
| setDestination(String) | yes | IATA code of destination airport, i.e. `SIN` |
| setFirstName(String) | yes | Given name or First name of passenger |
| setLastName(String) | yes | Surname or Last name of passenger |



## Example

```
Seats seats = new Seats();

SeatItem seatItem1 = new SeatItem();

seatItem1.setType("Extra Legroom");
seatItem1.setSeatNumber("4A");
seatItem1.setPrice(new BigDecimal("25.00"));
seatItem1.setCurrency("MYR");
seatItem1.setOrigin("KUL");
seatItem1.setDestination("SIN");
seatItem1.setFirstName("John");
seatItem1.setLastName("Smith");

seats.seatItemList.add(seatItem1);

//.. Continue add for other passenger and routes


Travlytix.Flight.Seats(seats);
Travlytix.send();
```

---

## **Insurance Event**

Send user selected insurance details with this event.

## Class


| Name | Type  | Description |
| :--- | :---  | :--- | 
| Insurances | Class | Insurance root |
| InsuranceItem | Class | Insurance details |


## Fields (in Insurances)

| Name | Type | Required | Description |
| :---| :--- | :--- | :--- |
| insuranceItemList | List<InsuranceItem> | yes | List of selected insurance details |



## Methods (in InsuranceItem)

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setName(String) | yes | Insurance name |
| setPrice(BigDecimal) | no | Insurance price |
| setCurrency(String) | no | ISO 4217 currency code |
| setOrigin(String) | yes | IATA code of origin airport, i.e. `KUL` |
| setDestination(String) | yes | IATA code of destination airport, i.e. `SIN` |
| setFirstName(String) | yes | Given name or First name of passenger |
| setLastName(String) | yes | Surname or Last name of passenger |


## Example

```
Insurances insurances = new Insurances();

InsuranceItem insuranceItem1 = new InsuranceItem();

insuranceItem1.setName("Full Protection");
insuranceItem1.setPrice(price);
insuranceItem1.setCurrency("MYR");
insuranceItem1.setOrigin("KUL");
insuranceItem1.setDestination("SIN");
insuranceItem1.setFirstName("John");
insuranceItem1.setLastName("Smith");

insurances.insuranceItemList.add(insuranceItem1);

//..Continue add for other passengers and routes

Travlytix.Flight.Insurances(insurances);
Travlytix.send();

```

---

## **Ancillaries Event**

Send user selected ancillaries details with this event.

## Class
| Name | Type  | Description |
| :--- | :---  | :--- | 
| Ancillaries | Class | Ancillaries root|
| AncillariesItem | Class | Ancillaries details |

## Fields (in Ancillaries)

| Name | Type | Required | Description |
| :---| :--- | :--- | :--- |
| ancillariesItemList | List\<AncillariesItem> | yes | List of selected ancillaries details |

## Methods (in AncillariesItem) 

| Name & Type | Required | Description |
| :---  | :--- | :--- | 
| setType(String) | yes | Ancillaries type, i.e. `Express Check-in`, `Internet` and etc |
| setName(String) | yes | Name of the selected ancillaries, i.e. `5MB Chat Internet`, `1GB Highspeed Internet` and etc  |
| setPrice(BigDecimal) | no | Ancillaries price |
| setCurrency(String) | no | ISO 4217 currency code |
| setOrigin(String) | yes | IATA code of origin airport |
| setDestination(String) | yes | IATA code of destination airport |
| setFirstName(String) | yes | Given name or First name of passenger |
| setLastName(String) | yes | Surname or Last name of passenger |


## Example


```
Ancillaries ancillaries = new Ancillaries();

AncillariesItem ancillariesItem1 = new AncillariesItem();

ancillariesItem1.setType("Express Check-in");
ancillariesItem1.setName("Check-in fast lane");
ancillariesItem1.setPrice(new BigDecimal("10.0"));
ancillariesItem1.setCurrency("MYR");
ancillariesItem1.setOrigin("KUL");
ancillariesItem1.setDestination("SIN");
ancillariesItem1.setFirstName("John");
ancillariesItem1.setLastName("Smith");

ancillaries.ancillariesItemList.add(ancillariesItem1);

//.. Continue add for other passengers & routes

Travlytix.Flight.Ancillaries(ancillaries);
Travlytix.send();
```

---


## **Payment Event**

## Class
| Name | Type  | Description |
| :--- | :---  | :--- | 
| Payment | Class | Payment details |
| Charges | Class | Charges details  |
| CardDetails | Class | Card details |
| Address | Class | Address details |
| Mobile | Class | Mobile details |
| Contact | Class | Contact details |



## Methods (in Payment)

| Name & Type | Required | Description |
| :---  | :--- | :--- |
| setCharges(Charges) | yes | Charges details |
| setCurrency(String) | yes | ISO 4217 currency code |
| setPaymentMethod(String) | yes | Payment method name |
| setCardDetails(CardDetails) | no | Credit/Debit/Charge card details |
| setTitle(String) | no | Title prefix of name, i.e. `Mr.`,`Mrs.`, `Miss` and etc. |
| setFirstName(String) | yes | Given name or First name of main passenger |
| setLastName(String) | yes | Surname or Last name of main passenger |
| setEmail(String) | yes | Email address |
| setAddress(Address) | no | Full Address details |
| setMobile(Mobile) | no | Mobile number details |
| setContact(Contact) | no | Contact number details |
| setNationality(String) | no | Country ISO 3166 code, i.e. `MYS` for Malaysia |



## Methods (in Charges)

| Name & Type | Required | Description |
| :---  | :--- | :--- |
| setTotal(BigDecimal) | yes | Total charges for the booking |
| setFare(BigDecimal) | no | Total fare charges for the booking |
| setTax(BigDecimal) | no | Total tax charges for the booking |
| setBaggage(BigDecimal) | no | Total baggage charges for the booking  |
| setSeats(BigDecimal) | no | Total seat charges for the booking |
| setInsurances(BigDecimal) | no | Total insurance charges for the  booking |
| setMeals(BigDecimal) | no | Total meals charges for the booking |
| setAncillaries(BigDecimal) | no | Total ancillaries charges for the booking |


## Constants (in CardDetails)

| Name | Type  | Description |
| :--- | :---  | :--- | 
| VISA | String | Use this to indicate visa card type |
| MASTERCARD | String | Use this to indicate mastercard type |


## Methods (in CardDetails)

| Name & Type | Required | Description |
| :---  | :--- | :--- |
| setType(String) | no | Name of the card type, i.e. `visa`, `mastercard` and etc  |
| setFirst6(String) | yes | Your card's first 6 digits |
| setLast4(String) | yes | Your card's last 4 digits |


## Methods (in Address)

| Name & Type | Required | Description |
| :---  | :--- | :--- |
| setCountry(String) | yes | Country ISO 3166 code, i.e. `MYS` for Malaysia |
| setCity(String) | yes | City name|
| setAddress1(String) | yes | Address line 1 |
| setAddress2(String)  | no | Address line 2 |
| setPostCode(String) | yes | Postal code |


## Methods (in Mobile)

| Name & Type | Required | Description |
| :---  | :--- | :--- |
| setCountryCode(String) | yes | Country code of mobile number, i.e. `+60` for Malaysia |
| setNumber(String) | yes | Mobile number without country code |
| setCountry(String) | no | Country ISO 3166 code, i.e. `MYS` for Malaysia |



## Methods (in Contact)

| Name & Type | Required | Description |
| :---  | :--- | :--- |
| setCountryCode(String) | yes | Country code of contact number, i.e. `+60` for Malaysia |
| setNumber(String) | yes | Contact number without country code |
| setCountry(String) | no | Country ISO 3166 code, i.e. `MYS` for Malaysia |


## Examples 

```
Payment payment = new Payment();

Charges charges = new Charges();
charges.setTotal(new BigDecimal("280.50"));
charges.setFare(new BigDecimal("200.50"));
charges.setTax(new BigDecimal("50"));
charges.setBaggage(new BigDecimal("6"));
charges.setSeats(new BigDecimal("6"));
charges.setInsurances(new BigDecimal("6"));
charges.setMeals(new BigDecimal("6"));
charges.setAncillaries(new BigDecimal("6"));

payment.setCharges(charges);
payment.setCurrency("MYR");
payment.setPaymentMethod("Credit Card");


CardDetails cardDetails = new CardDetails();
cardDetails.setType(CardDetails.VISA);
cardDetails.setFirst6("411111");
cardDetails.setLast4("1111");

payment.setCardDetails(cardDetails);

payment.setTitle("Mr.");
payment.setFirstName("John");
payment.setLastName("Smith");
payment.setEmail("john@travlytix.com");

Address address = new Address();
address.setCountry("MYS");
address.setCity("Kuala Lumpur");
address.setAddress1("58, Mid valley");
address.setAddress2("Near LRT Station");
address.setPostCode("58000");

payment.setAddress(address);

Mobile mobile = new Mobile();
mobile.setCountryCode("+60");
mobile.setNumber("11357777");
mobile.setCountry("MYS");

payment.setMobile(mobile);

Contact contact = new Contact();
contact.setCountryCode("+60");
contact.setNumber("555555");
contact.setCountry("MYS");

payment.setContact(contact);

payment.setNationality("MYS");


Travlytix.Flight.Payment(payment);
Travlytix.send()
```

---


## **Confirm Event**

## Class 

| Name | Type  | Description |
| :--- | :---  | :--- | 
| PaymentResponse | Class | PaymentResponse |
| TicketItem | Class | Ticket details |


## Constants (in PaymentResponse)

| Name | Type  | Description |
| :--- | :---  | :--- | 
| SUCCESS | String | Use this to indicate success booking |
| PENDING | String | Use this to indicate pending booking |
| FAILED | String | Use this to indicate failed booking |

## Fields (in PaymentResponse)

| Name | Type | Required | Description |
| :---| :--- | :--- | :--- |
| ticketItemList | List\<TicketItem> | yes | List of ticket details |

## Methods (in PaymentResponse)

| Name & Type | Required | Description |
| :---  | :--- | :--- |
| setPnr(String) | yes | Passenger name record of the booking |
| setStatus(String) | yes | Status of the booking, Must be either `successful`, `pending` or `failed` |

## Methods (in TicketItem)

| Name & Type | Required | Description |
| :---  | :--- | :--- |
| setTicketNumber(String) | yes | E-Ticket number |
| setFlightOperator(String) | no | Flight Operator code |
| setFlightNumber(String) | yes | Flight number, i.e. `123` |
| setDepartureAirport(String) | yes | IATA code of departure airport, i.e. `KUL` |
| setArrivalAirport(String) | yes | IATA code of arrival airport, i.e. `SIN` |
| setDepartureDatetime(String) | yes | Departure date and time of the flight segment, i.e. `2019-01-15T12:10:00` |
| setArrivalDatetime(String) | yes | Arrival date and time of the flight segment, i.e. `2019-01-15T13:10:00` |
| setFirstName(String) | yes | Given name or First name of passenger |
| setLastName(String) | yes | Surname or Last name of passenger |

## Example 

```
PaymentResponse paymentResponse = new PaymentResponse();

paymentResponse.setPnr("PNRPNR");
paymentResponse.setStatus(PaymentResponse.SUCCESS);

TicketItem departureTicketItem = new TicketItem();
departureTicketItem.setTicketNumber("123");
departureTicketItem.setFlightOperator("XX");
departureTicketItem.setFlightNumber("101");
departureTicketItem.setDepartureAirport("KUL");
departureTicketItem.setArrivalAirport("SIN");
departureTicketItem.setDepartureDatetime("2019-01-15T12:10:00");
departureTicketItem.setArrivalDatetime("2019-01-15T13:10:00");
departureTicketItem.setFirstName("John");
departureTicketItem.setLastName("Smith");
paymentResponse.ticketItemList.add(departureTicketItem);

TicketItem returnTicketItem = new TicketItem();
returnTicketItem.setTicketNumber("143");
returnTicketItem.setFlightOperator("YY");
returnTicketItem.setFlightNumber("105");
returnTicketItem.setDepartureAirport("SIN");
returnTicketItem.setArrivalAirport("KUL");
returnTicketItem.setDepartureDatetime("2019-01-20T12:10:00");
returnTicketItem.setArrivalDatetime("2019-01-20T13:10:00");
returnTicketItem.setFirstName("John");
returnTicketItem.setLastName("Smith");

paymentResponse.ticketItemList.add(returnTicketItem);

Travlytix.Flight.Confirm(paymentResponse);
Travlytix.send();

```

### **Note:** 
After you create the each request, you should need to call the `Travlytix.send()` method to send details to travlytix api. It is applicable to all travlytix events.

---



