##Goal 

Parsing the HTML code of every URL that has been identified as an article

##Input

Gets URL from django app from table ```articles``` where column ```processed_html_parser```=```false```

##Output

*	Gives a JSON file to django app with fields ```url``` and ```html```, which saves ```html```, ```processed_html_parser=timestamp``` to table articles, where ```url```=URL

##Technical Implementation

Out of the two options, newspaper3k and boilerpipe, newspaper3k seems a better choice since boilerpipe isn't it maintained by the developer anymore. As soon as we get banned by the domain, we route the URLs of that specific domain to *[Crawlera](http://scrapinghub.com/crawlera/)*. 

This way we avoid unnecessarily consuming the requests we can have at Crawlera. For most blogs and websites it should work just fine with our own crawlers.

Don't forget errorlogging of failed URLs, so we can reparse if necessary.