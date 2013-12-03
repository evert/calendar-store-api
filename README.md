#SchedJoules Calendar Store API
With this API you can get access to the SchedJoules Public Calendar Library. SchedJoules delivers the most comprehensive public desktop, web and mobile calendar store in the world. We currently deliver over 180.000 complete, accurate and timely public calendars for holidays, sports, weather and financial events. We do so in 40 languages.

##Set yourself up
1. Mail us at info@schedjoules.com for an API key
2. Try from your terminal.

````curl -L 'https://api.schedjoules.com/pages/115676?locale=en&location=ar' -v -H 'Authorization: Token token="{api_key}"'

If you get data you are good to go. Else contact us so we can help you out.

##Making a request
* All requests start with https://api.schedjoules.com/
* We use REST methodology for the API
* All output  is in JSON format
* Appending URLs with .json is not mandatory
* The API only accepts HTTPS requests

````GET /pages/{page_id}&locale={[ISO 639-1 code](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)}&location={[ISO_3166 code](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)}
````
````Required GET parameters
````* page_id
````
````Optional GET parameters
````* locale - Default is 'en'
````* location - Default is 'us'

If you use the locale and location parameter you will overwrite the page\_id and you will be redirected to the correct page_id. So have you application detect the users locale and location and the API will return the page with the calendars that are most relevant to the user in his preferred language ;-)

###Headers
####Versioning
The API version needs to be set in the request header. Current version is: `v1`. If you don't set headers and the default version is bumped your application might not function. Labels can be added without version change so make your client flexible enough to handle that. Follow our [twitter feed](http://twitter.com/schedjoules) for latest SchedJoules' news also on the API. We'll email you with API changes as well once you are set up.

This API is in Beta. That means that the structure and labels will remain as-is unless there are moyor reasons to change them. As of January 1st 2014 the API will be production ready. One thing that we do need to make to big progress on is the documentation. So hack away and keep those questions coming.

####Authentication
You will need an API key to use this API. You can get your API key by contacting us at info@schedjoules.com. You need to set the API key in the header.

###Pages
The API is mainly build around the concept of pages. Visualise a page in your application for eg football.That page would have all the name of all the teams in a league from which users can select the calendar they want to add to their calendar.

A page has a name has some meta data like its name and page\_section. Think of page sections as headers or paragraphes. A page section has a name. Within the page\_section are the items wich have an item\_class. And item\_ class is either a 'calendar' or a 'page'.

A page is, not very surprisingly, a child page of the page the user is looking at. Think of English Football being a (sub)page of All Football and Premier League being a (sub)page of English Football.

An item\_class calendar is where the magic happens. This is where the users get to see the actual data in calendar file and can add that calendar to his calendar.

##Just to make sure there is no misunderstandig ... 
By using our API it is clear to you that all the data you access is proprietary. The data and images can not be used for any other purpose then agreed upon. Data can't be stored in any database other than on a users client for performance purposes.

##Caching
Do your clients, yourself and us a favor and cache where you can. It will speed up you app and save bandwidth.
* All requests we return will include an `ETag` or `Last-Modified` header so use `If-Modified-Since` and `If-None-Matched` in you requests.
* Icons urls that are in the JSON have their ETag mentioned in de response.

##Rate limits
There are no rate limits. We do count requests. If we think we can help you improve we will contact you.

##Help Us
Please tell us how we can make the API better. If you have a specific feature request or if you found a bug, please use GitHub issues or send us an email.