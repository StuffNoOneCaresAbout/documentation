##### GET `/api/v1/videos/:id`
> Schema:  
```
{
  "title": String,
  "videoId": String,
  "videoThumbnails": [
    {    
      "quality": String,
      "url": String,
      "width": Int32,
      "height": Int32
    },
  ],

  "description": String,
  "descriptionHtml": String,
  "published": Int64,
  "publishedText": String,
  
  "keywords": Array(String),
  "viewCount": Int64,
  "likeCount": Int32,
  "dislikeCount": Int32,
  
  "isFamilyFriendly": Bool,
  "allowedRegions": Array(String),
  "genre": String,
  "genreUrl": String,
 
  "author": String,
  "authorId": String,
  "authorUrl": String,

  "lengthSeconds": Int32,
  "allowRatings": Bool,
  "rating": Float32,
  "isListed": Bool,
  "hlsUrl": String?,

  "adaptiveFormats": [
    {
      "index": String,
      "bitrate": String,
      "init": String,
      "url": String,
      "itag": String,
      "type": String,
      "clen": String,
      "lmt": String,
      "projectionType": Int32,
      "container": String,
      "encoding": String,
      "qualityLabel": String?,
      "resolution": String?
    },
  ],
  "formatStreams": [
    {
      "url": String,
      "itag": String,
      "type": String,
      "quality": String,
      "container": String,
      "encoding": String,
      "qualityLabel": String,
      "resolution": String,
      "size": String
    }, 
  ],
  "captions": [
    {
      "label": String,
      "languageCode": String,
      "url": String,
    },
  ],
  "recommendedVideos": [
    {
      "videoId": String,
      "title": String,
      "videoThumbnails": [
        {
          "quality": String,
          "url": String,
          "width": Int32,
          "height": Int32
        },
      ],
      "author": String,
      "lengthSeconds": Int32,
      "viewCountText" String
    }
  ]
}
```

##### GET `/api/v1/trending`
> Schema:
```
[
  {
    "title": String,
    "videoId": String,
    "videoThumbnails": [
      {
        "quality": String,
        "url": String,
        "width": Int32,
        "height" Int32
    ],

    "lengthSeconds": Int32,
    "viewCount": Int64,

    "author": String,
    "authorId": String,
    "authorUrl": String,

    "published": Int64,
    "publishedText": String,
    "description": String,
    "descriptionHtml": String
  }
]
```

##### GET `/api/v1/top`
> Schema:
```
[
  {
    "title": String,
    "videoId": String,
    "videoThumbnails": [
      {
        "quality": String,
        "url": String,
        "width": Int32,
        "height" Int32
    ],

    "lengthSeconds": Int32,
    "viewCount": Int64,

    "author": String,
    "authorId": String,
    "authorUrl": String,

    "published": Int64,
    "publishedText": String,
    "description": String,
    "descriptionHtml": String
  }
]
```

##### GET `/api/v1/channels/:ucid`
> Schema:
```
{
  "author": String,
  "authorId": String,
  "authorUrl": String,
  "authorBanners": [
    {
      "url": String,
      "width": Int32,
      "height": Int32
    }
  ],
  "authorThumbnails": [
    {
      "url": String,
      "width": Int32,
      "height": Int32
    }
  ],
  
  "subCount": Int32,
  "totalViews": Int64,
  "joined": Int64,
  "paid": Bool,
  "isFamilyFriendly": Bool,
  "description": String,
  "descriptionHtml": String,
  "allowedRegions": Array(String),
  "latestVideos": [
    {
      "title": String,
      "videoId": String,
      "author": String,
      "authorId": String,
      "authorUrl": String,

      "videoThumbnails": [
        {
          "quality": String,
          "url": String,
          "width": Int32,
          "height": Int32
        }
      ],
      "description": String,
      "descriptionHtml": String,
      "viewCount": Int64,
      "published": Int64,
      "publishedText": String,
      "lengthSeconds": Int32
    }
  ]
}
```

##### GET `/api/v1/channels/:ucid/videos`
> Schema:
```
[
  {
    "title": String,
    "videoId": String,
    "author": String,
    "authorId": String,
    "authorUrl": String,

    "videoThumbnails": [
      {
        "quality": String,
        "url": String,
        "width": Int32,
        "height": Int32
      }
    ],
    "description": String,
    "descriptionHtml": String,

    "viewCount": Int64,
    "published": Int64,
    "publishedText": String,
    "lengthSeconds": Int32
  }
]
```

Parameters:
```
page: Int32
```

##### GET `/api/v1/search`
> Schema:
```
[
  {
    "type": "video",
    "title": String,
    "videoId": String,
    "author": String,
    "authorId": String,
    "authorUrl": String,
    "videoThumbnails": [
      {
        "quality": String,
        "url": String,
        "width": Int32,
        "height": Int32
      }
    ],
    "description": String,
    "descriptionHtml": String,
    "viewCount": Int64,
    "published": Int64,
    "publishedText": String,
    "lengthSeconds": Int32,
    "liveNow": Bool
  },
  {
    "type": "playlist",
    "title": String,
    "playlistId": String,
    "author": String,
    "authorId": String,
    "authorUrl": String,
    
    "videoCount": Int32,
    "videos": [
      "title": String,
      "videoId": String,
      "lengthSeconds": Int32,
      "videoThumbnails": [
        {
          "quality": String,
          "url": String,
          "width": Int32,
          "height": Int32
        }
      ]
    ]
  },
  {
    "type": "channel",
    "author": String,
    "authorId": String,
    "authorUrl": String,

    "authorThumbnails": [
      {
        "url": String,
        "width": Int32,
        "height": Int32
      }
    ],
    "subCount": Int32,
    "videoCount": Int32,
    "description": String,
    "descriptionHtml": String,
  }
]
```

Parameters
```
q: String,
page: Int32,
sort_by: "relevance", "rating", "upload_date", "view_count"
date: "hour", "today", "week", "month", "year"
duration: "short", "long"
type: "video", "playlist", "channel", "all", (default: video)
```

##### GET `/api/v1/captions/:id`
> Schema:
```
{
  "captions": [
    {
      "label": String,
      "languageCode": String
    }
  ]
}
```

Parameters
```
label: String
```

A request with `label` will return the selected captions in WebVTT format.


##### GET `/api/v1/comments/:id`
> Schema:
```
{
  "commentCount": Int32?,
  "comments": [
    {
      "author": String,
      "authorThumbnails": [
        "url": String,
        "width": Int32,
        "height": Int32
      ],
      "authorId": String,
      "authorUrl": String,

      "content": String,
      "contentHtml": String,
      "published": Int64,
      "publishedText": String,
      "likeCount": Int32,
      "commentId": String,
       
      "replies": {
        "replyCount": Int32,
        "continuation": String
      }?
    }
  ],
  "continuation": String?
}
```

Parameters:
```
continuation: String
```