ADZUNA API GUIDELINES AND EXAMPLES

Search
Use this endpoint to retrieve Adzuna's job advertisement listings.

Visit the Interactive Endpoint Documentation for full technical details and a playground to make test calls.

Example #1: Simple jobs query
To get twenty "Javascript Developer" jobs in the whole of UK, in JSON format, issue a GET request to:

http://api.adzuna.com/v1/api/jobs/gb/search/1?app_id={5687583093a44630affd1f5641b1f291}&app_key={YOUR API KEY}&results_per_page=20&what=javascript%20developer&content-type=application/json
The response (certain long fields have been cropped in the example below) looks something like:

{
  "__CLASS__": "Adzuna::API::Response::JobSearchResults",
  "results": [
    {
      "salary_min": 50000,
      "longitude": -0.776902,
      "location": {
        "__CLASS__": "Adzuna::API::Response::Location",
        "area": [
          "UK",
          "South East England",
          "Buckinghamshire",
          "Marlow"
        ],
        "display_name": "Marlow, Buckinghamshire"
      },
      "salary_is_predicted": 0,
      "description": "JavaScript Developer Corporate ...",
      "__CLASS__": "Adzuna::API::Response::Job",
      "created": "2013-11-08T18:07:39Z",
      "latitude": 51.571999,
      "redirect_url": "http://adzuna.co.uk/jobs/land/ad/129698749...",
      "title": "Javascript Developer",
      "category": {
        "__CLASS__": "Adzuna::API::Response::Category",
        "label": "IT Jobs",
        "tag": "it-jobs"
      },
      "id": "129698749",
      "salary_max": 55000,
      "company": {
        "__CLASS__": "Adzuna::API::Response::Company",
        "display_name": "Corporate Project Solutions"
      },
      "contract_type": "permanent"
    },
    ... another 19 ads here ...
  ]
}
Example #2: Complex jobs query
There are lots of parameters you can use to enhance your query. In this example, we want javascript developers with salaries over 50k (salary_min=50000), full time (full_time=1) and permanent (permanent=1) positions, to reduce ambiguity we exclude any ads that contain the keyword "Java" (what_exclude=java), we limit the results to London (where=london) and we sort by salary (sort_by=salary). The resulting GET call:

http://api.adzuna.com:80/v1/api/jobs/gb/search/1?app_id={95c2c47e}&app_key={5687583093a44630affd1f5641b1f291}&results_per_page=20&what=javascript%20developer&what_exclude=java&where=london&sort_by=salary&salary_min=30000&full_time=1&permanent=1&content-type=application/json
will return:

{
  "__CLASS__": "Adzuna::API::Response::JobSearchResults",
  "results": [
    {
      "salary_min": 55000,
      "location": {
        "__CLASS__": "Adzuna::API::Response::Location",
        "area": [
          "UK",
          "London",
          "Central London",
          "The City"
        ],
        "display_name": "The City, Central London"
      },
      "salary_is_predicted": 0,
      "description": "...  and experience with more than one language a distinct advantage (python/ruby/perl/javascript/erlang).The Senior Developer Python will be involved in helping us to scale up and develop ...",
      "__CLASS__": "Adzuna::API::Response::Job",
      "created": "2013-10-23T19:32:43Z",
      "redirect_url": "http://adzuna.co.uk/jobs/land/ad/126977586?v=712F911142DFEF191FB2F0E068CD2734177B7F7E&utm_medium=api&utm_source=6eda9a47",
      "contract_time": "full_time",
      "title": "Senior Developer Python",
      "category": {
        "__CLASS__": "Adzuna::API::Response::Category",
        "label": "IT Jobs",
        "tag": "it-jobs"
      },
      "id": "126977586",
      "salary_max": 55000,
      "company": {
        "__CLASS__": "Adzuna::API::Response::Company",
        "display_name": "Exposed Solutions Limited"
      },
      "contract_type": "permanent"
    },
    ... up to another 19 ads here ...
  ]
}
There are many query parameters you can use to limit or enhance the data you retrieve. Visit the interactive API reference for a full list.
