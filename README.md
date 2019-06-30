# webcrawler
Use scrapy to crawl title, url, image-url, ingredients and text of german recipe pages:

|| Domain | succesfully scraped | total number of recipes      |
|-|-------------------|----------------------------:|-------:|
|1| www.chefkoch.de | 80.000 | 330.000 |
|2| www.ichkoche.at| 0 | 150.000|
|3| www.daskochrezept.de| 0 | 87.000|
|4| www.eatsmarter.de | 1.000  | 83.000 |
|5| www.lecker.de | 120 | 60.000 |
|6| www.essen-und-trinken.de | 500 | 30.000 |
|7| www.womenshealth.de| 330 | 2.000 |
|8| www.rapunzel.de | 0 | ??? |
|9| www.springlane.de|0|???|
|10| www.proveg.com|0|???|
|11| www.eat-this.org|0|???|
|12| www.veganheaven.de|0|???|
|13| www.youtube.de|0|???|

## Local run

1. build image
    ```bash
    docker build .
    ```
    
2. run image 
    ```bash
    docker run --env SPIDER_NAME=ChefkochSypder image
    ```

## Deploy to Openshift

1. verify your logged in and select the correct namespace
    ```bash
    $ oc projects
    $ oc project *namespace*
    ```
    
2. start build with
    ```bash
    $ oc start-build washeuteessen-crawler --from-dir=. --follow
    ```

3. verify result
    ```bash 
    $ oc describe dc/washeuteessen-crawler
    
    ...
    Deployment #3 (latest):
    	Name:		washeuteessen-crawler-X
    	Created:	2 minutes ago
    	Status:		Active
    ...
    
    ```
