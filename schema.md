## Roku Search feed - JSON schema

Developers can use the Roku Search feed 2.0 JSON schema to validate the format of their search feed (it, however, does not guarantee that a feed will be validated by Roku). This schema may occasionally be updated by Roku.

```
{
    "$schema": "http://json-schema.org/draft-07/schema#",
    "type": "object",
    "properties": {
        "version": {
            "type": "string"
        },
        "defaultLanguage": {
            "$ref": "#/definitions/language_type"
        },
        "defaultAvailabilityCountries": {
            "type": "array",
            "items": [
                {
                    "$ref": "#/definitions/country_type"
                }
            ]
        },
        "assets": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "id": {
                        "type": "string"
                    },
                    "type": {
                        "$ref": "#/definitions/asset_type"
                    },
                    "externalIdSource": {

                    },
                    "titles": {
                        "type": "array",
                        "items": {
                            "type": "object",
                            "properties": {
                                "value": {
                                    "type": "string",
                                    "maxLength": 200
                                },
                                "language": {
                                    "$ref": "#/definitions/language_type"
                                }
                            },
                            "required": [
                                "value"
                            ]
                        }
                    },
                    "shortDescriptions": {
                        "type": "array",
                        "items": {
                            "type": "object",
                            "properties": {
                                "value": {
                                    "type": "string",
                                    "maxLength": 200
                                },
                                "language": {
                                    "$ref": "#/definitions/language_type"
                                }
                            },
                            "required": [
                                "value"
                            ]
                        }
                    },
                    "longDescriptions": {
                        "type": "array",
                        "items": {
                            "type": "object",
                            "properties": {
                                "value": {
                                    "type": "string",
                                    "maxLength": 500
                                },
                                "language": {
                                    "$ref": "#/definitions/language_type"
                                }
                            },
                            "required": [
                                "value"
                            ]
                        }
                    },
                    "releaseDate": {
                        "type": "string",
                        "pattern": "^[0-9]{4}-[0-9]{2}-[0-9]{2}$"
                    },
                    "releaseYear": {
                        "type": "integer"
                    },
                    "genres": {
                        "type": "array",
                        "items": {
                            "$ref": "#/definitions/genre_type"
                        }
                    },
                    "advisoryRatings": {
                        "type": "array",
                        "items": {
                            "type": "object",
                            "properties": {                                
                                "source": {
                                    "$ref": "#/definitions/advisory_ratings_source_type"
                                },
                                "value": {
                                    "type": "string"
                                },
                                "descriptors": {
                                    "type": "array"
                                }
                            },
                            "allOf": [
                                {
                                    "if": {
                                        "properties": {
                                            "source": {
                                                "const": "BBFC"
                                            }
                                        }
                                    },
                                    "then": {
                                        "properties": {
                                            "value": {
                                                "$ref" : "#/definitions/BBFC_values"
                                            },
                                            "descriptors": {
                                                "items": {
                                                    "$ref": "#/definitions/BBFC_descriptors"
                                                }
                                            }
                                        }
                                    }
                                },
                                {
                                    "if": {
                                        "properties": {
                                            "source": {
                                                "const": "CLASSIND"
                                            }
                                        }
                                    },
                                    "then": {
                                        "properties": {
                                            "value": {
                                                "$ref" : "#/definitions/CLASSIND_values"
                                            },
                                            "descriptors": {
                                                "items": {
                                                    "$ref": "#/definitions/CLASSIND_descriptors"
                                                }
                                            }
                                        }
                                    }
                                },
                                {
                                    "if": {
                                        "properties": {
                                            "source": {
                                                "const": "CHVRS"
                                            }
                                        }
                                    },
                                    "then": {
                                        "properties": {
                                            "value": {
                                                "$ref" : "#/definitions/CHVRS_values"
                                            },
                                            "descriptors": {
                                                "items": {
                                                    "$ref": "#/definitions/CHVRS_descriptors"
                                                }
                                            }
                                        }
                                    }
                                },
                                {
                                    "if": {
                                        "properties": {
                                            "source": {
                                                "enum": ["FSF", "FSK"]
                                            }
                                        }
                                    },
                                    "then": {
                                        "properties": {
                                            "value": {
                                                "$ref" : "#/definitions/FSF_FSK_values"
                                            }
                                        }
                                    }
                                },
                                {
                                    "if": {
                                        "properties": {
                                            "source": {
                                                "const": "MPAA"
                                            }
                                        }
                                    },
                                    "then": {
                                        "properties": {
                                            "value": {
                                                "$ref" : "#/definitions/MPAA_values"
                                            },
                                            "descriptors": {
                                                "items": {
                                                    "$ref": "#/definitions/MPAA_descriptors"
                                                }
                                            }
                                        }
                                    }
                                },
                                {
                                    "if": {
                                        "properties": {
                                            "source": {
                                                "const": "RTC"
                                            }
                                        }
                                    },
                                    "then": {
                                        "properties": {
                                            "value": {
                                                "$ref" : "#/definitions/RTC_values"
                                            },
                                            "descriptors": {
                                                "items": {
                                                    "$ref": "#/definitions/RTC_descriptors"
                                                }
                                            }
                                        }
                                    }
                                },
                                {
                                    "if": {
                                        "properties": {
                                            "source": {
                                                "const": "USA_PR"
                                            }
                                        }
                                    },
                                    "then": {
                                        "properties": {
                                            "value": {
                                                "$ref" : "#/definitions/USA_PR_values"
                                            },
                                            "descriptors": {
                                                "$ref": "#/definitions/USA_PR_descriptors"
                                            }
                                        }
                                    }
                                }
                            ],
                            "required": [
                                "source",
                                "value"
                            ]
                        }
                    },
                    "images": {
                        "type": "array",
                        "items": {
                            "type": "object",
                            "properties": {
                                "type": {
                                    "$ref": "#/definitions/image_type"
                                },
                                "url": {
                                    "type": "string",
                                    "pattern": "^http(s)?://.+$"
                                },
                                "languages": {
                                    "type": "array",
                                    "$ref": "#/definitions/language_type"
                                }
                            },
                            "required": [
                                "type",
                                "url"
                            ]
                        }
                    },
                    "durationInMilliseconds": {
                        "type": "number"
                    },
                    "durationInSeconds": {
                        "type": "integer"
                    },
                    "credits" : {
                        "type": "array",
                        "items": {
                            "type": "object",
                            "properties": {
                                "name" : {
                                    "type": "string"
                                },
                                "role" : {
                                    "type": "string"
                                },
                                "birthDate": {
                                    "type":"string"
                                },
                                "deathDate": {
                                    "type":"string"
                                },
                                "imageUrl": {
                                    "type":"string"
                                }
                            }
                        }
                    },
                    "episodeInfo": {
                        "type": "object",
                        "properties": {
                            "seriesId": {
                                "type": "string"
                            },
                            "seasonNumber": {
                                "type": "integer"
                            },
                            "episodeNumber": {
                                "type": "integer"
                            }
                        },
                        "required": [
                            "seriesId",
                            "episodeNumber"
                        ]
                    },
                    "seasonInfo": {
                        "type": "object",
                        "properties": {
                            "seasonNumber": {
                                "type": "integer"
                            },
                            "seriesId": {
                                "type": "string"
                            }
                        },
                        "required": [
                            "seasonNumber",
                            "seriesId"
                        ]
                    },
                    "content": {
                        "type": "object",
                        "properties": {
                            "playOptions": {
                                "type": "array",
                                "items": {
                                    "type": "object",
                                    "properties": {
                                        "license": {
                                            "$ref": "#/definitions/license_type"
                                        },
                                        "price": {
                                            "type": "number"
                                        },
                                        "quality": {
                                            "$ref": "#/definitions/video_quality_type"
                                        },
                                        "currency": {
                                            "type": "string"
                                        },
                                        "playId": {
                                            "type": "string",
                                            "minLength": 2
                                        },
                                        "availabilityStartTimeStamp": {
                                            "type": "number"
                                        },
                                        "availabilityEndTimeStamp": {
                                            "type": "number"
                                        }
                                    },
                                    "allOf": [
                                        {
                                            "if": {
                                                "properties": {
                                                    "license": {
                                                        "enum" : ["rental", "purchase"] 
                                                    }
                                                }
                                            },
                                            "then": {
                                                "required": ["price"]
                                            }
                                        },
                                        {
                                            "if" : {
                                                "properties": {
                                                    "license": {
                                                        "enum" : ["free", "subscription"]
                                                    }
                                                }
                                            },
                                            "then" : {
                                                "not": {"required": ["price"]}                                                
                                            }
                                        }
                                    ],
                                    "required": [
                                        "license",                                        
                                        "quality",
                                        "playId"
                                    ]
                                }
                            }
                        },
                        "required": [
                            "playOptions"
                        ]
                    }
                },
                "if": {
                    "properties": {
                        "type": {
                            "const": "externalIdOnly"
                        }
                    },
                    "required": [
                        "type"
                    ]
                },
                "then": {
                    "required": [
                        "id",
                        "type",
                        "externalIdSource",
                        "content"
                    ]
                },
                "else": {
                    "required": [
                        "id",
                        "titles",
                        "type",
                        "content"
                    ]
                },
                "anyOf": [
                    {
                        "required": [
                            "releaseDate"
                        ]
                    },
                    {
                        "required": [
                            "releaseYear"
                        ]
                    }
                ]
            }
        }
    },
    "required": [
        "version",
        "assets"
    ],
    "definitions": {
        "asset_type": {
            "type": "string",
            "enum": [
                "movie",
                "series",
                "season",
                "episode",
                "shortForm",
                "externalIdOnly"
            ]
        },
        "genre_type": {
            "type": "string",
            "enum": [
                "action",
                "action sports",
                "adventure",
                "aerobics",
                "agriculture",
                "animals",
                "animated",
                "anime",
                "anthology",
                "archery",
                "arm wrestling",
                "art",
                "arts/crafts",
                "artistic gymnastics",
                "artistic swimming",
                "athletics",
                "auction",
                "auto",
                "auto racing",
                "aviation",
                "awards",
                "badminton",
                "ballet",
                "baseball",
                "basketball",
                "3x3 basketball",
                "beach soccer",
                "beach volleyball",
                "biathlon",
                "bicycle",
                "bicycle racing",
                "billiards",
                "biography",
                "blackjack",
                "bmx racing",
                "boat",
                "boat racing",
                "bobsled",
                "bodybuilding",
                "bowling",
                "boxing",
                "bullfighting",
                "bus./financial",
                "canoe",
                "card games",
                "ceremony",
                "cheerleading",
                "children",
                "children-music",
                "children-special",
                "children-talk",
                "collectibles",
                "comedy",
                "comedy drama",
                "community",
                "computers",
                "canoe/kayak",
                "consumer",
                "cooking",
                "cricket",
                "crime",
                "crime drama",
                "curling",
                "cycling",
                "dance",
                "dark comedy",
                "darts",
                "debate",
                "diving",
                "docudrama",
                "documentary",
                "dog racing",
                "dog show",
                "dog sled",
                "drag racing",
                "drama",
                "educational",
                "entertainment",
                "environment",
                "equestrian",
                "erotic",
                "event",
                "exercise",
                "fantasy",
                "faith",
                "fashion",
                "fencing",
                "field hockey",
                "figure skating",
                "fishing",
                "football",
                "food",
                "fundraiser",
                "gaelic football",
                "game show",
                "gaming",
                "gay/lesbian",
                "golf",
                "gymnastics",
                "handball",
                "health",
                "historical drama",
                "history",
                "hockey",
                "holiday",
                "holiday music",
                "holiday music special",
                "holiday special",
                "holiday-children",
                "holiday-children special",
                "home improvement",
                "horror",
                "horse",
                "house/garden",
                "how-to",
                "hunting",
                "hurling",
                "hydroplane racing",
                "indoor soccer",
                "interview",
                "intl soccer",
                "judo",
                "karate",
                "kayaking",
                "lacrosse",
                "law",
                "live",
                "luge",
                "martial arts",
                "medical",
                "military",
                "miniseries",
                "mixed martial arts",
                "modern pentathlon",
                "motorcycle",
                "motorcycle racing",
                "motorsports",
                "mountain biking",
                "music",
                "music special",
                "music talk",
                "musical",
                "musical comedy",
                "mystery",
                "nature",
                "news",
                "newsmagazine",
                "olympics",
                "opera",
                "outdoors",
                "parade",
                "paranormal",
                "parenting",
                "performing arts",
                "playoff sports",
                "poker",
                "politics",
                "polo",
                "pool",
                "pro wrestling",
                "public affairs",
                "racquet",
                "reality",
                "religious",
                "ringuette",
                "road cycling",
                "rodeo",
                "roller derby",
                "romance",
                "romantic comedy",
                "rowing",
                "rugby",
                "running",
                "rhythmic gymnastics",
                "sailing",
                "science",
                "science fiction",
                "self improvement",
                "shooting",
                "shopping",
                "sitcom",
                "skateboarding",
                "skating",
                "skeleton",
                "skiing",
                "snooker",
                "snowboarding",
                "snowmobile",
                "soap",
                "soap special",
                "soap talk",
                "soccer",
                "softball",
                "special",
                "speed skating",
                "sport climbing",
                "sports",
                "sports talk",
                "squash",
                "standup",
                "sumo wrestling",
                "surfing",
                "suspense",
                "swimming",
                "table tennis",
                "taekwondo",
                "talk",
                "technology",
                "tennis",
                "theater",
                "thriller",
                "track/field",
                "track cycling",
                "travel",
                "trampoline",
                "triathlon",
                "variety",
                "volleyball",
                "war",
                "water polo",
                "water skiing",
                "watersports",
                "weather",
                "weightlifting",
                "western",
                "wrestling",
                "yacht racing"
            ]
        },
        "license_type": {
            "type": "string",
            "enum": [
                "free",
                "subscription",
                "rental",
                "purchase"
            ]
        },
        "advisory_ratings_source_type": {
            "type": "string",
            "enum": [
                "BBFC",
                "CLASSIND",
                "CHVRS",
                "CPR",
                "FSF",
                "FSK",
                "MPAA",
                "RTC",
                "USA_PR"
            ]
        },
        "language_type": {
            "type": "string",
            "enum": [
                "de",
                "de-de",
                "en",
                "en-us",
                "en-gb",
                "en-ie",
                "en-ca",
                "es",
                "es-us",
                "es-mx",
                "es-ar",
                "es-bo",
                "es-cl",
                "es-co",
                "es-cr",
                "es-ec",
                "es-sv",
                "es-gt",
                "es-hn",
                "es-ni",
                "es-pa",
                "es-pe",
                "pt-br",
                "pt"
            ]
        },
        "country_type": {
            "type": "string",
            "enum": [
                "ar",
                "bo",
                "cl",
                "co",
                "ec",
                "sv",
                "gt",
                "hn",
                "ni",
                "pa",
                "pe",
                "br",
                "ca",
                "de",
                "gb",
                "ie",
                "mx",
                "us"
            ]
        },
        "video_quality_type": {
            "type": "string",
            "enum": [
                "sd",
                "hd",
                "hd+",
                "uhd"
            ]
        },
        "image_type": {
            "type": "string",
            "enum": [
                "main",
                "background"
            ]
        },
        "BBFC_descriptors": {
            "type": "string",
            "description": "Descriptors for BBFC ratings",
            "enum": [
                "theme",
                "behaviour",
                "horror",
                "nudity",
                "discrimination",
                "language",
                "violence",
                "drugs",
                "sex"
            ]
        },        
        "BBFC_values": {
            "type": "string",
            "enum": [
                "U",
                "PG",                
                "12-A",
                "12",
                "15",
                "18",
                "R18",
                "R-18"
            ]
        },
        "CHVRS_descriptors": {
            "type": "string",
            "description": "Descriptors for CHVRS ratings",
            "enum": [
                "not recommended for young children",
                "not recommended for children",
                "frightening scenes",
                "mature theme",
                "coarse language",
                "crude content",
                "nudity",
                "sexual content",
                "violence",
                "disturbing content",
                "substance abuse",
                "gory scenes",
                "explicit sexual content",
                "brutal violence",
                "sexual violence",
                "language may offend"
            ]
        },
        "CHVRS_values": {
            "type": "string",
            "enum": [
                "G",
                "PG",                
                "14-A",                
                "18-A",
                "R",
                "E"
            ]
        },
        "CLASSIND_descriptors": {
            "type": "string",
            "description": "Descriptors for CLASSIND ratings",
            "enum": [
                "violência",
                "violência extrema",
                "conteúdo sexual",
                "nudez",
                "sexo",
                "sexo explícito",
                "drogas",
                "drogas lícitas",
                "drogas ilícitas",
                "linguagem imprópria",
                "atos criminosos",
                "onteúdo impactante"
            ]
        },
        "CLASSIND_values": {
            "type": "string",
            "enum": [
                "L",
                "10",
                "12",
                "14",
                "16",
                "18"
            ]
        },
        "MPAA_descriptors": {
            "type": "string",
            "description": "Descriptors for MPAA ratings",
            "enum": [
                "AC",
                "AL",
                "GL",
                "MV",
                "V",
                "GV",
                "BN",
                "N",
                "SSC",
                "RP"
            ]
        },
        "MPAA_values": {
            "type": "string",
            "enum": [
                "G",
                "PG",                
                "PG-13",
                "R",
                "NC-17",                
                "UR"
            ]
        },
        "RTC_descriptors": {
            "type": "string",
            "description": "Descriptors for RTC ratings",
            "enum": [
                "violence",
                "sex",
                "language",
                "drugs"
            ]
        },
        "RTC_values": {
            "type": "string",
            "enum": [
                "AA",
                "A",
                "B",
                "B-15",                
                "C",
                "D"
            ]
        },
        "USA_PR_descriptors": {
            "type": "string",
            "description": "Descriptors used for USA_PR ratings",
            "enum": [
                "D",
                "L",
                "S",
                "V",
                "FV"
            ]
        },
        "USA_PR_values": {
            "type": "string",
            "enum": [
                "TV-Y",                
                "TV-Y7",                
                "TV-G",                
                "TV-PG",                
                "TV-14",                
                "TV-MA"                
            ]
        },
        "FSF_FSK_values": {
            "type": "string",
            "enum": [
                "0",
                "6",
                "12",
                "16",
                "18"
            ]
        }
    }
}
```
