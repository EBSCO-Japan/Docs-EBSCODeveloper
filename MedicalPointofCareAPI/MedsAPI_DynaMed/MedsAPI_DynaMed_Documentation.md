# MedsAPI Dynamed Documentation

Searching DynaMed Content

Basic Search

The DynaMed API GET /search endpoint allows you to search DynaMed content.  The search endpoint provides five parameters for specifying the search criteria: the query term, the publication type Id, the page, the page token and language.  The query term is the word that you are searching for in the language specified.  The publication type id(s) are the type(s) of publications to return.  Page information can also be specified.  The page is the next page of results to start from.  Each page contains 10 items.  The page token is needed for a paginated search.  It is returned in the first page of results.  Only the search query term is required.

To Perform a Basic Search (example):

Gather the following information for the request:

An access token. Please see Use the Client Credentials Grant for further information.
A word or phrase to search.
Request

GET 'https://apis.ebsco.com/medsapi-dynamed/v1/search?query=heart%20attack&pubTypeId=drug&pubTypeId=condition'
The search above is for the URL encoded words heart and attack within the publication types drug and condition.

Note: The search engine removes punctuation. Therefore, a search for heart attack is equivalent to a search for "heart attack" with no preference for the order of terms.  Also, when using Curl, the pubTypeId can be specified as a comma separated list:  &pubTypeId=drug,condition.

Adding the initiatedBy query parameter to the request will override the default value for both the response and the transaction logs. The following are possible values for the initiatedBy query parameter: "autocomplete", "autocorrect-override-link", "didyoumean-link", "typed-in", "voice-to-text".

Response

Note:  The response below is not a complete response.  It has been truncated to highlight relevant fields.


{
  "_metadata": {
    "initiatedBy": "typed-in",
    "presentedAs": "result-list",
    "pageToken": "id:rsid:22a054fe-f2e3-4caf-88ee-2a3d2b651679",
    "searchTime": 205,
    "totalItems": 942,
    "queryUsed": "heart attack",
    "pageSize": 10,
    "totalPages": 95,
    "page": 1,
    "aggregations": [
      {
        "field": "pubTypeId",
        "counts": {
          "condition": 395,
          "drug": 547
        }
      }
    ],
    "request": {
      "query": "heart attack",
      "pubTypeIds": [
        "drug%2C condition"
      ]
    },
    "links": [
      {
        "rel": "self",
        "href": "https://apis.ebsco.com/medsapi-dynamed/v1/search?query=heart%20attack&pubTypeId=drug%2C%20condition"
      },
      {
        "rel": "first",
        "href": "https://apis.ebsco.com/medsapi-dynamed/v1/search?query=heart%20attack&pubTypeId=drug%2C%20condition&pageToken=id:rsid:22a054fe-f2e3-4caf-88ee-2a3d2b651679&page=1"
      },
      {
        "rel": "last",
        "href": "https://apis.ebsco.com/medsapi-dynamed/v1/search?query=heart%20attack&pubTypeId=drug%2C%20condition&pageToken=id:rsid:22a054fe-f2e3-4caf-88ee-2a3d2b651679&page=95"
      },
      {
        "rel": "next",
        "href": "https://apis.ebsco.com/medsapi-dynamed/v1/search?query=heart%20attack&pubTypeId=drug%2C%20condition&pageToken=id:rsid:22a054fe-f2e3-4caf-88ee-2a3d2b651679&page=2"
      },
      {
        "rel": "pubTypes",
        "href": "https://apis.ebsco.com/medsapi-dynamed/v1/pubTypes"
      }
    ]
  },
  "items": [
    {
      "id": "T916967",
      "toc": [
        {
          "title": "Overview and Recommendations",
          "anchor": "GUID-1717F8A2-2C34-4B48-9402-23886B9187DE"
        },
        {
          "title": "Etiology and Pathogenesis",
          "anchor": "GUID-F5F98554-4292-4C25-BDA1-E6C0270593E1"
        },
-
-
-
        {
          "title": "References",
          "anchor": "GUID-BD7F9F70-F6D2-4ED4-A0A5-DEF6057FAC35"
        }
      ],
      "title": "Complications of Myocardial Infarction",
      "description": "The majority of complications present within 24 hours after acute myocardial infarction, with most others occurring within 7 days.",
      "slug": "/condition/complications-of-myocardial-infarction",
      "sections": [
        {
          "anchor": "EMBOLIC_AND_BLEEDING_COMPLICATIONS_AFTER_MYOCARDIAL_INFARCTION",
          "path": [
            "Prognosis ",
            "Embolic and bleeding complications after myocardial infarction"
          ],
          "title": "Embolic and bleeding complications after myocardial infarction"
        },
        {
          "anchor": "INFLAMMATORY_COMPLICATIONS_AFTER_MYOCARDIAL_INFARCTION",
          "path": [
            "Prognosis "
          ],
          "title": "Inflammatory complications after myocardial infarction"
        },
        {
          "anchor": "ELECTRICAL_COMPLICATIONS_AFTER_MYOCARDIAL_INFARCTION",
          "path": [
            "Prognosis ",
            "Electrical complications after myocardial infarction"
          ],
          "title": "Electrical complications after myocardial infarction"
        }
      ],
      "pubType": {
        "title": "Condition"
      },
      "links": [
        {
          "rel": "self",
          "href": "https://apis.ebsco.com/medsapi-dynamed/v1/articles/T916967"
        }
      ]
    },

.
.
.

    {
      "id": "T114250",
      "toc": [
        {
          "title": "Overview and Recommendations",
          "anchor": "GUID-3F4AC031-291E-48FC-B1F2-BF34E2F4314D"
        },
-
-
-
        {
          "title": "References",
          "anchor": "GUID-E33F5BF6-7FD6-4E1D-A98F-CB76D9CFECB5"
        }
      ],
      "title": "Hypercholesterolemia",
      "description": "Hypercholesterolemia is a condition characterized by elevated serum levels of total and low-density lipoprotein (LDL) cholesterol.",
      "slug": "/condition/hypercholesterolemia",
      "sections": [],
      "pubType": {
        "title": "Condition"
      },
      "links": [
        {
          "rel": "self",
          "href": "https://apis.ebsco.com/medsapi-dynamed/v1/articles/T114250"
        }
      ]
    }
  ]
}

The response is composed of two sections: _metadata and items. The _metadata section contains information about the results.  The _metadata section has a searchTime.  The searchTime is the number of milliseconds for the actual search.  It does not reflect network latency.  The _metadata section also contains a request section that identifies the original request made by the caller.  The items array will be formatted as either image or non-image items (conditions, drugs etc).   If the image items are mixed with non-image items, the items will still have the format appropriate for an image or non-image.  The items are sorted by best match order regardless of the order that publication type ids specified.  See the Non-Image Response Details and Image Response Details sections below for more information.

 

Searching with a Non-English Query Term

Use the queryLanguage parameter to search for a query term from a non-english language.  The queryLanguage parameter uses the 2 letter country codes from ISO 639-1 to specify the language.  For example, the country code 'fr' specifies the language French.

To Perform a Non-English Query Term Search (example):

Gather the information for the request:

An access token. Please see Use the Client Credentials Grant for further information.
A non-english word or phrase to search.  In the case below, the query is for coeur, the french word for heart.
The country code for the language that you are using to search.  In the case below, 'fr' is used to specify French.
Note:  The query word coeur is URL encoded.

Request

GET 'https://apis.ebsco.com/medsapi-dynamed/v1/search?query=%0Ac%C5%93ur&queryLanguage=fr&pubTypeId=condition&pubTypeId=drug'
Response

The response will come back in English with the results that match the criteria.  The request section of the response will indicate the query specified by the request.  In this example, the request section will indicate 'cœur'.  The _metadata  section queryUsed will indicate the English word that it actually searched for.  In this example, the queryUsed is 'heart'.  If no translation is needed, then both fields would be set to 'heart'.

If a valid language code was specified and no equivalent English term is found, the original term submitted will be used in the search.

 

What to Expect When a Query Does Not Match

The search engine attempts to find the best possible matches for any query term or query phrase.  If a word is misspelled in a phrase, the engine will use its medical knowledge base to find all permutations in order to determine the most likely intention of the search.  The response will indicate in the _metadata section initiatedBy field that the response reflects a Did You Mean ("didyoumean-probe") query. 

If no matches can be found, an empty item list will be returned and the initiatedBy field will be "typed-in".

Request

GET 'https://apis.ebsco.com/medsapi-dynamed/v1/search?query=kwsdewasfwer&pubTypeId=condition&pubTypeId=drug
Response (example when the query term or phrase in the Request does not match)


{
    "_metadata": {
        "initiatedBy": "typed-in",
        "totalItems": 0,
        "queryUsed": "kwsdewasfwer",
        "page": 1,
        "pageSize": 0,
    "request": {
        "query": "kwsdewasfwer",
        "pubTypeIds": [
            "condition",
            "drug"
        ]
    },
    "items": []
}
 

Retrieving Paginated Results

Results that come back from the search engine are paginated.  In the initial response of paginated results, the page field in the _metadata section indicates the next page to start with.  The total item count is the pageSize field in the _metadata section (or less if at the end of the results).  A token, returned in the initial response, must be passed to the API to continue the search.  The token is found in the pageToken field in the _metadata section.  The value of the token has no particular meaning to the caller.  The initiatedBy field found in the _metadata section of the response will be set to "paging" when paging information is included in the request parameters.  As a convenience, the results also include the HATEAOS links for retrieving the first, last, previous, next and the pubTypeIds.

To Retrieve the Next Page After the Initial Search Request (example):

Request

GET 'https://apis.ebsco.com/medsapi-dynamed/v1/search?query=%0Ac%C5%93ur&queryLanguage=fr&pubTypeId=condition&pubTypeId=drug&pageToken=id:rsid:7b111036-5e79-4d9d-bfb1-5a416c31e781&page=11'
Response

Note:  The response below is not a complete response.  It has been truncated to highlight the relevant fields.


 "_metadata": {
        "pageToken": "id:rsid:eea02f73-9596-4861-9ea7-beb8e5f390e6",
        "totalItems": 2289,
        "queryUsed": "heart",
        "page": 21,          // The next page to GET would be page 21
        "pageSize": 10,      // Each page will contain 10 items (or less if no more results are 
                             // found on the last page)
        "totalPages": 229,   // You would need to make 229 search calls to see all the results.  
                             // Each subsequent page would contain less relevant content.
        "links": [
            {
                "rel": "self",
                "href": "https://apis.ebsco.com/medsapi-dynamed/v1/search?query=heart&pubTypeId=condition&pubTypeId=drug&pageToken=id%3Arsid%3Aeea02f73-9596-4861-9ea7-beb8e5f390e6&page=11"
            },
            {
                "rel": "first",
                "href": "https://apis.ebsco.com/medsapi-dynamed/v1/search?query=heart&pubTypeId=condition&pubTypeId=drug&pageToken=id:rsid:eea02f73-9596-4861-9ea7-beb8e5f390e6&page=1&pageSize=10"
            },
            {
                "rel": "last",
                "href": "https://apis.ebsco.com/medsapi-dynamed/v1/search?query=heart&pubTypeId=condition&pubTypeId=drug&pageToken=id:rsid:eea02f73-9596-4861-9ea7-beb8e5f390e6&page=229&pageSize=10"
            },
            {
                "rel": "next",
                "href": "https://apis.ebsco.com/medsapi-dynamed/v1/search?query=heart&pubTypeId=condition&pubTypeId=drug&pageToken=id:rsid:eea02f73-9596-4861-9ea7-beb8e5f390e6&page=21&pageSize=10"
            },
            {
                "rel": "prev",
                "href": "https://apis.ebsco.com/medsapi-dynamed/v1/search?query=heart&pubTypeId=condition&pubTypeId=drug&pageToken=id:rsid:eea02f73-9596-4861-9ea7-beb8e5f390e6&page=11&pageSize=10"
            },
            {
                "rel": "pubTypes",
                "href": "https://apis.ebsco.com/medsapi-dynamed/v1/pubTypes"
            }
        ]
    },
    "request": {
        "query": "heart",
        "pubTypeIds": [
            "condition",
            "drug"
        ],
        "pageToken": "id%3Arsid%3Aeea02f73-9596-4861-9ea7-beb8e5f390e6",
        "page": "20"  // The page that is requested
    }
 
 

Retrieving DynaMed Content for Specific Publication Types

The DynaMed search endpoint can be used to query for specific types of publications.  The list of supported publication type IDs can be retrieved using the medsapi-dynamed/v1/pubtypes endpoint.  If no pubTypeIds are specified when using the search endpoint, then content for all of the publication type ids will be searched.

To Retrieve DynaMed Content for Specific Publication Types (example):

Gather the information for the request:

An access token. Please see Use the Client Credentials Grant for further information.
A word or phrase to search.  
The publication type ID desired.
Request

GET 'https://apis.ebsco.com/medsapi-dynamed/v1/search?query=heart%20attack&pubTypeId=drug&pubTypeId=condition'
Response

Note:  The response below is not a complete response.  It has been truncated to highlight the relevant fields.


 "_metadata": {
        "aggregations": [
            {
                "field": "pubTypeId",
                "counts": {
                    "condition": 1147,  // 1147 items matched the "condition" term
                    "drug": 1142	// 1142 items matched the "drug" term
                }
            }
        ],

"items": [
        {

            "title": "Ventricular Arrhythmias",
            "description": "Ventricular arrhythmias are arrhythmias characterized by rapid ventricular rhythms, often due to underlying cardiac conditions.",
            "pubType": {
                "title": "Condition"
            },

       }
The response will include an aggregation count for each pubTypeId that was specified.  Each item will indicate the type of publication type that it was found in.  If non matches were found, the count will be 0 for the pubTypeId.

 

Non-Media Response Details

Each item, with the exception of image and video results, will contain the following information:


{
   "id": "T193266",						// ID of the resource
   "toc": [							// Table of Contents with an array of Titles for 
                                                                // each section and anchor GUIDs to locate within the article
      {
           "title": "Overview and Recommendations",
           "anchor": "GUID-5250DF0A-CBA8-416F-B438-11F7BBE324AF"
      },
   ],
   "title": "Heart Failure With Preserved Ejection Fraction",	// Title of the article
								// The description shows a snippet of the text 
                                                                // that matched
   "description": "Heart failure with preserved ejection fraction refers to clinical heart failure with a left ventricular ejection fraction ≥ 50%.",
   "slug": "/condition/heart-failure-with-preserved-ejection-fraction",
   "sections": [						// Section(s) whose titles matched the query terms
       {
           "anchor": "CARDIAC",
           "path": [
               "History and Physical ",
               " Physical ",
               "Cardiac"
           ],
           "title": "Cardiac"
       }
   ],
   "pubType": {
       "title": "Condition"					// publication type ID of this item
   },
   "links": [							// Link to the item that matched
       {
           "rel": "self",
           "href": "https://apis.ebsco.com/medsapi-dynamed/v1/articles/T193266"
        }
   ]
}
 

Image Response Details

 An image response contains a link to a full resolution image that is optimized for the browser making the request.  The image link is only valid for 24 hours.  An image response will contain the following information:


 {
     "id": "I509101",					                // ID of the image
     "title": "Left parasternal long axis view of heart.",		// Title of the image
     "links": [							        // Link to get the image
         {
             "rel": "external",
             "href": "http://media.ebsco.healthcare/eis-live/image/authenticated/f_auto/v1/EBSCOHealth/CCMS/I509101?__cld_token__=exp=1590236397~hmac=cb9faf1f9188138b0d1c73944bc70c2d75c605a84e599a5af07139d35db8375f"
        }
     ],
     "contentLocations": [						// An array of article locations where the image is used
         {
             "parent": {
                 "title": "Ultrasound in the Intensive Care Unit (ICU)",
                 "slug": "/evaluation/ultrasound-in-the-intensive-care-unit-icu"
             },
             "anchor": "I509101"
         }
     ]
}
 

Video Response Details

 A video response contains a link to a video. The video link is only valid for 24 hours.  A video response will contain the following information:


{
  "id": "V1622166482467",
  "title": "Recognizing Transfusion-Related Acute Lung Injury (TRALI).",
  "format": "mp4",
  "description": "This video shows...",
  "links": [
    {
      "rel": "external",
      "href": "http://media.ebsco.healthcare/eis-live/video/authenticated/v1/EBSCOHealth/videos/V1622166482467?__cld_token__=exp=1589920019~hmac=318fc29d454df2a4f122307ee5"
    }
  ],
  "contentLocations": [
    {
      "parent": {
        "title": "Asthma in Adults and Adolescents",
        "slug": "/condition/asthma-in-adults-and-adolescents"
      },
      "anchor": "V1622166355451"
    }
  ]
}

 

Error Response Codes

The DynaMed search endpoint can return one of the error response codes.


