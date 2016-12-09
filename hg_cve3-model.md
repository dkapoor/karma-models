## hg_cve-for-karma.jl

### PyTransforms

### Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _#text_ | `memex:cvssComplexity` | `memex:CVSS1`|
| _cve_ | `uri` | `memex:Vulnerability1`|
| _timestamp_ | `schema:startDate` | `memex:Vulnerability1`|


### Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Vulnerability1` | `memex:hasCVSS` | `memex:CVSS1`|
