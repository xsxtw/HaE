## BurpSuite Highlighter and Extractor

HaE is used to highlight HTTP requests and extract information from `HTTP response messages` or `request messages`.

## Public Rules

```yaml
rules:
- rule:
  - color: green
    engine: dfa
    loaded: true
    name: Shrio
    regex: (=deleteMe|rememberMe=)
    scope: any
  - color: green
    engine: dfa
    loaded: true
    name: OSS
    regex: ([A|a]ccess[K|k]ey[I|i][d|D]|[A|a]ccess[K|k]ey[S|s]ecret)
    scope: any
  - color: green
    engine: dfa
    loaded: true
    name: JSON Web Token
    regex: (ey[A-Za-z0-9_-]{10,}\.[A-Za-z0-9._-]{10,}|ey[A-Za-z0-9_\/+-]{10,}\.[A-Za-z0-9._\/+-]{10,})
    scope: any
  - color: green
    engine: dfa
    loaded: true
    name: Amazon Web Services(AWS)
    regex: ((AKIA[0-9A-Z]{16})|(s3\.amazonaws.com[/]+|[a-zA-Z0-9_-]*\.s3\.amazonaws.com))
    scope: any
  type: Fingerprint
- rule:
  - color: yellow
    engine: nfa
    loaded: true
    name: Email
    regex: (([a-zA-Z0-9][_|\.])*[a-zA-Z0-9]+@([a-zA-Z0-9][-|_|\.])*[a-zA-Z0-9]+\.((?!js|css|jpg|jpeg|png|ico)[a-zA-Z]{2,}))
    scope: response
  - color: orange
    engine: nfa
    loaded: true
    name: Chinese IDCard
    regex: '[^0-9]((\d{8}(0\d|10|11|12)([0-2]\d|30|31)\d{3}$)|(\d{6}(18|19|20)\d{2}(0[1-9]|10|11|12)([0-2]\d|30|31)\d{3}(\d|X|x)))[^0-9]'
    scope: response
  - color: orange
    engine: nfa
    loaded: true
    name: Chinese Mobile Number
    regex: '[^0-9A-Za-z](1(3([0-35-9]\d|4[1-8])|4[14-9]\d|5([\d]\d|7[1-79])|66\d|7[2-35-8]\d|8\d{2}|9[89]\d)\d{7})[^0-9A-Za-z]'
    scope: response
  - color: cyan
    engine: nfa
    loaded: true
    name: Internal IP Address
    regex: '[^0-9]((127\.0\.0\.1)|(localhost)|(10\.\d{1,3}\.\d{1,3}\.\d{1,3})|(172\.((1[6-9])|(2\d)|(3[01]))\.\d{1,3}\.\d{1,3})|(192\.168\.\d{1,3}\.\d{1,3}))'
    scope: response
  type: Basic Information
- rule:
  - color: gray
    engine: nfa
    loaded: false
    name: newName
    regex: newRegex
    scope: any
  type: New 0

```
