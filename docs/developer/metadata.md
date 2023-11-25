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
	"name": "Yggdrasil",
	"description": "Yggdrasil is an immense mythical tree that connects the nine worlds in Norse cosmology.",
	"image": "ipfs://QmYggdrasilImageHash123",
	"properties": {
		"simple_property": "new value",
		"custom_property": {
			"name": "Custom Property",
			"value": "Custom Value",
			"display_value": "This is a custom property.",
			"class": "custom-class",
			"css": {
				"color": "#ff9900",
				"font-size": "16px",
				"font-weight": "normal"
			}
		},
		"another_array_property": {
			"name": "Another Array",
			"value": [5,6,7,8],
			"class": "another-class"
		}
	}
}

```
