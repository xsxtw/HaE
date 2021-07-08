## BurpSuite Highlighter and Extractor

HaE is used to highlight HTTP requests and extract information from `HTTP response messages` or `request messages`.

## Public Rules

```yaml
rules:
- rule:
  - color: green
    engine: dfa
    loaded: true
    name: Shiro
    regex: (=deleteMe|rememberMe=)
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
    name: Swagger UI
    regex: ((swagger-ui.html)|(\"swagger\":)|(Swagger UI)|(swaggerUi))
    scope: response
  type: Fingerprint
- rule:
  - color: yellow
    engine: nfa
    loaded: true
    name: Email
    regex: (([a-zA-Z0-9][_|\.])*[a-zA-Z0-9]+@([a-zA-Z0-9][-|_|\.])*[a-zA-Z0-9]+\.((?!js|css|jpg|jpeg|png|ico)[a-zA-Z]{2,}))
    scope: response body
  - color: orange
    engine: nfa
    loaded: true
    name: Chinese IDCard
    regex: '[^0-9]((\d{8}(0\d|10|11|12)([0-2]\d|30|31)\d{3}$)|(\d{6}(18|19|20)\d{2}(0[1-9]|10|11|12)([0-2]\d|30|31)\d{3}(\d|X|x)))[^0-9]'
    scope: response body
  - color: orange
    engine: nfa
    loaded: true
    name: Chinese Mobile Number
    regex: '[^0-9A-Za-z](1(3([0-35-9]\d|4[1-8])|4[14-9]\d|5([\d]\d|7[1-79])|66\d|7[2-35-8]\d|8\d{2}|9[89]\d)\d{7})[^0-9A-Za-z]'
    scope: response body
  - color: cyan
    engine: nfa
    loaded: true
    name: Internal IP Address
    regex: '[^0-9]((127\.0\.0\.1)|(localhost)|(10\.\d{1,3}\.\d{1,3}\.\d{1,3})|(172\.((1[6-9])|(2\d)|(3[01]))\.\d{1,3}\.\d{1,3})|(192\.168\.\d{1,3}\.\d{1,3}))'
    scope: response
  - color: green
    engine: nfa
    loaded: true
    name: MAC Address
    regex: (^([a-fA-F0-9]{2}(:[a-fA-F0-9]{2}){5})|[^a-zA-Z0-9]([a-fA-F0-9]{2}(:[a-fA-F0-9]{2}){5}))
    scope: response
  - color: orange
    engine: nfa
    loaded: false
    name: Chinese Bank Card ID
    regex: '[^0-9]([1-9]\d{12,18})[^0-9]'
    scope: response
  type: Basic Information
- rule:
  - color: cyan
    engine: dfa
    loaded: true
    name: RCE Paramters
    regex: ((cmd=)|(exec=)|(command=)|(execute=)|(ping=)|(query=)|(jump=)|(code=)|(reg=)|(do=)|(func=)|(arg=)|(option=)|(load=)|(process=)|(step=)|(read=)|(function=)|(feature=)|(exe=)|(module=)|(payload=)|(run=)|(daemon=)|(upload=)|(dir=)|(download=)|(log=)|(ip=)|(cli=))
    scope: request
  - color: yellow
    engine: dfa
    loaded: true
    name: Java Deserialization
    regex: (javax.faces.ViewState)
    scope: response
  - color: cyan
    engine: dfa
    loaded: true
    name: Debug Logic Parameters
    regex: ((access=)|(adm=)|(admin=)|(alter=)|(cfg=)|(clone=)|(config=)|(create=)|(dbg=)|(debug=)|(delete=)|(disable=)|(edit=)|(enable=)|(exec=)|(execute=)|(grant=)|(load=)|(make=)|(modify=)|(rename=)|(reset=)|(root=)|(shell=)|(test=)|(toggl=))
    scope: request
  - color: cyan
    engine: nfa
    loaded: true
    name: URL As A Value
    regex: (=(https?://.*|https?%3(a|A)%2(f|F)%2(f|F).*))
    scope: request
  type: Maybe Vulnerability
- rule:
  - color: green
    engine: dfa
    loaded: true
    name: OSS
    regex: ([A|a]ccess[K|k]ey[I|i][d|D]|[A|a]ccess[K|k]ey[S|s]ecret)
    scope: any
  - color: green
    engine: nfa
    loaded: true
    name: Amazon AWS URL
    regex: (((([a-zA-Z0-9._-]+\.s3|s3)(\.|\-)+[a-zA-Z0-9._-]+|[a-zA-Z0-9._-]+\.s3|s3)\.amazonaws\.com)|(s3:\/\/[a-zA-Z0-9-\.\_]+)|(s3.console.aws.amazon.com\/s3\/buckets\/[a-zA-Z0-9-\.\_]+)|(amzn\.mws\.[0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12})|(ec2-[0-9-]+.cd-[a-z0-9-]+.compute.amazonaws.com)|(us[_-]?east[_-]?1[_-]?elb[_-]?amazonaws[_-]?com))
    scope: any
  - color: green
    engine: nfa
    loaded: true
    name: Amazon AWS AccessKey ID
    regex: ((aws(.{0,20})?(?-i)['\"][0-9a-zA-Z\/+]{40}['\"])|((A3T[A-Z0-9]|AKIA|AGPA|AIDA|AROA|AIPA|ANPA|ANVA|ASIA)[a-zA-Z0-9]{16}))
    scope: any
  - color: green
    engine: nfa
    loaded: true
    name: Amazon AWS Region
    regex: ((us(-gov)?|ap|ca|cn|eu|sa)-(central|(north|south)?(east|west)?)-\d)
    scope: any
  - color: yellow
    engine: nfa
    loaded: true
    name: SSH Private Key
    regex: ([-]+BEGIN [^\s]+ PRIVATE KEY[-])
    scope: response
  type: Sensitive Information
- rule:
  - color: gray
    engine: nfa
    loaded: false
    name: Linkfinder
    regex: (?:"|')(((?:[a-zA-Z]{1,10}://|//)[^"'/]{1,}\.[a-zA-Z]{2,}[^"']{0,})|((?:/|\.\./|\./)[^"'><,;|*()(%%$^/\\\[\]][^"'><,;|()]{1,})|([a-zA-Z0-9_\-/]{1,}/[a-zA-Z0-9_\-/]{1,}\.(?:[a-zA-Z]{1,4}|action)(?:[\?|#][^"|']{0,}|))|([a-zA-Z0-9_\-/]{1,}/[a-zA-Z0-9_\-/]{3,}(?:[\?|#][^"|']{0,}|))|([a-zA-Z0-9_\-]{1,}\.(?:php|asp|aspx|jsp|json|action|html|js|txt|xml)(?:[\?|#][^"|']{0,}|)))(?:"|')
    scope: any
  type: Other

```
