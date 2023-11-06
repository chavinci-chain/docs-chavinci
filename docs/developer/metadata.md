# Token metadata

This document contains JSON schema specification for Chavinci token metadata which can be stored inside IPFS. It's and loosely based on "ERC-1155 Metadata URI JSON Schema".

Schema:

```JSON
{
    "title": "Token Metadata",
    "type": "object",
    "properties": {
        "name": {
            "type": "string",
            "description": "Identifies the name of given token."
        },
        "description": {
            "type": "string",
            "description": "Describes the token and its purpose."
        },
        "image": {
            "type": "string",
            "description": "A URI pointing to a resource with mime type image/* representing the asset to which this token represents. Consider making any images at a width between 320 and 1080 pixels and aspect ratio between 1.91:1 and 4:5 inclusive."
        },
        "properties": {
            "type": "object",
            "description": "Arbitrary properties. Values may be strings, numbers, object or arrays."
        }
    }
}
```

Example data:

```JSON
{
	"name": "Mjölnir",
	"description": "Mjölnir is the hammer of the thunder god Thor in Norse mythology, used both as a devastating weapon and as a divine instrument to provide blessings.",
	"image": "ipfs://QmeJPx9UpmyZ4536oSp4cNb9C1aSX4PzT8n9mrYppQ2KrN",
	"properties": {
		"simple_property": "example value",
		"rich_property": {
			"name": "Name",
			"value": "123",
			"display_value": "123 Example Value",
			"class": "emphasis",
			"css": {
				"color": "#ffffff",
				"font-weight": "bold",
				"text-decoration": "underline"
			}
		},
		"array_property": {
			"name": "Name",
			"value": [1,2,3,4],
			"class": "emphasis"
		}
	}
}
```