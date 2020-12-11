## BurpSuite Highlighter and Extractor

HaE is used to highlight HTTP requests and extract information from `HTTP response messages` or `request messages`.

## Public Rules

```json
{
	"Chinese Mobile Number": {
		"loaded": true,
		"regex": "[^0-9](1(3([0-35-9]\\d|4[1-8])|4[14-9]\\d|5([0125689]\\d|7[1-79])|66\\d|7[2-35-8]\\d|8\\d{2}|9[89]\\d)\\d{7})[^0-9]",
		"color": "orange",
		"engine": "nfa",
		"scope": "response",
		"action": "any"
	},
	"Amazon Web Services(AWS)": {
		"loaded": true,
		"regex": "((AKIA[0-9A-Z]{16})|(s3\\.amazonaws.com[/]+|[a-zA-Z0-9_-]*\\.s3\\.amazonaws.com))",
		"color": "green",
		"engine": "dfa",
		"scope": "any",
		"action": "any"
	},
	"Email": {
		"loaded": true,
		"regex": "(([a-zA-Z0-9][_|\\.])*[a-zA-Z0-9]+@([a-zA-Z0-9][-|_|\\.])*[a-zA-Z0-9]+\\.((?!js|css|jpg|jpeg|png|ico)[a-zA-Z]{2,}))",
		"color": "yellow",
		"engine": "nfa",
		"scope": "response",
		"action": "any"
	},
	"Shiro": {
		"loaded": true,
		"regex": "(=deleteMe|rememberMe=)",
		"color": "green",
		"engine": "dfa",
		"scope": "any",
		"action": "any"
	},
	"Chinese IDCard": {
		"loaded": true,
		"regex": "[^0-9]((\\d{8}(0\\d|10|11|12)([0-2]\\d|30|31)\\d{3}$)|(\\d{6}(18|19|20)\\d{2}(0[1-9]|10|11|12)([0-2]\\d|30|31)\\d{3}(\\d|X|x)))[^0-9]",
		"color": "orange",
		"engine": "nfa",
		"scope": "response",
		"action": "any"
	},
	"Alibaba OSS": {
		"loaded": false,
		"regex": "([A|a]ccess[K|k]ey[I|i]d|[A|a]ccess[K|k]ey[S|s]ecret)",
		"color": "green",
		"engine": "dfa",
		"scope": "any",
		"action": "any"
	}
}
```
