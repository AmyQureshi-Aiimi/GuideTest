# Query Builders

One way to write InsightMaker queries is using the query builder helper objects available as part of the library. All query builder objects support the python and (&), or (|) and not (\~) logical operators allowing for plenty of flexibility.&#x20;

## SubQuery <a href="#subquery" id="subquery"></a>

`SubQuery(method, content)`\
All helpers inherit from the base class, SubQuery. It has two key properties, method and content, corresponding to a key, value pair, i.e. {method: content}. It implements the following functions:

`SubQuery.query_json()` \
The most important method of SubQuery, this returns the query wrapped in a [Bool Query](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/query-dsl-bool-query.html), suitable for use with the DS API.

`SubQuery.json()` \
The query without a bool wrapper.

`SubQuery.content_json()`\
The query json for the content element of this SubQuery only.

`SubQuery.append(other)`\
Append another SubQuery of equivalent method to the content of this SubQuery. (This exists primarily to assist the logical operator overload functions)

`SubQuery.merge(new_content)`\
Append additional content to the content of this SubQuery. (This exists primarily to assist the logical operator overload functions)

`SubQuery.is_bool_occurence()` \
Is this SubQuery of method “must”, “filter”, “should” or “must\_not”, all of which must exist within a Bool Query. (This exists primarily to assist the logical operator overload functions)

***

## BoolQuery <a href="#boolquery" id="boolquery"></a>

`BoolQuery(occurrences, minimum_should_match=1)`\
A way to logically combine other SubQuery objects. You shouldn't need to create these as using the logical operators and (&), or (|) and not (\~) on SubQuery objects will automatically create them for you. [Elastic Query DSL reference](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/query-dsl-bool-query.html).

<table><thead><tr><th width="210.06646728515625"></th><th width="100.076416015625">Type</th><th>Description</th></tr></thead><tbody><tr><td>occurrences</td><td>list</td><td>A list of SubQuery objects of method: “must”, “filter”, “should” or “must_not”</td></tr><tr><td>minimum_should_match</td><td>numeric</td><td>The number or percentage of should clauses returned documents must match. Default: 1</td></tr></tbody></table>

***

## FieldQuery <a href="#fieldquery" id="fieldquery"></a>

`FieldQuery(field, values)`\
An Elastic Query DSL [Terms Query](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/query-dsl-terms-query.html), it returns documents where a given field matches certain values.

<table><thead><tr><th width="99.939697265625">Name</th><th width="99.7467041015625">Type</th><th>Description</th></tr></thead><tbody><tr><td>field</td><td>string</td><td>The name of the field to match on</td></tr><tr><td>values</td><td>list</td><td>A list of values (of appropriate type) to match the field on</td></tr></tbody></table>

***

## ExistsQuery <a href="#existsquery" id="existsquery"></a>

`ExistsQuery(field)`\
Filters to documents where a non-null/empty value exists for the given field. [Reference](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/query-dsl-exists-query.html).

<table><thead><tr><th width="99.67669677734375">Name</th><th width="99.992919921875">Type</th><th>Description</th></tr></thead><tbody><tr><td>field</td><td>string</td><td>The name of the field to check</td></tr></tbody></table>

***

## RegexQuery <a href="#regexquery" id="regexquery"></a>

`RegexQuery(field, expression, flags=None, max_determined_states=None)`\
An Elastic Query DSL [Regular Expression Query](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/query-dsl-regexp-query.html).

<table><thead><tr><th width="209.516845703125">Name</th><th width="99.8675537109375">Type</th><th>Description</th></tr></thead><tbody><tr><td>field</td><td>string</td><td>The name of the field to check</td></tr><tr><td>expression</td><td>string</td><td>The regular expression string</td></tr><tr><td>flags</td><td>string</td><td>Optional - | separated flags of ALL <em>(default)</em>, ANYSTRING, COMPLEMENT, EMPTY, INTERSECTION, INTERVAL, or NONE. As <a href="https://lucene.apache.org/core/4_9_0/core/org/apache/lucene/util/automaton/RegExp.html">defined by Lucene</a>.</td></tr><tr><td>max_determined_states</td><td>integer</td><td>Optional – A way of limiting the number of execution states for regex matches, useful for more complex regular expressions. Elasticsearch default: 10,000.</td></tr></tbody></table>

***

## WildcardQuery <a href="#wildcardquery" id="wildcardquery"></a>

`WildcardQuery(field, wildcard)`\
An Elastic Query DSL [Wildcard Query](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/query-dsl-wildcard-query.html). Slightly simpler than a full blown regular expression query, just using \* to match zero or more characters.

<table><thead><tr><th width="99.96014404296875">Name</th><th width="99.9930419921875">Type</th><th>Description</th></tr></thead><tbody><tr><td>field</td><td>string</td><td>The name of the field to check</td></tr><tr><td>wildcard</td><td>string</td><td>The wildcard string to use</td></tr></tbody></table>

***

## PrefixQuery <a href="#prefixquery" id="prefixquery"></a>

`PrefixQuery(field, prefix)`\
An Elastic Query DSL [Prefix Query](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/query-dsl-prefix-query.html). Used to match documents where a field starts with a given string.

<table><thead><tr><th width="99.66705322265625">Name</th><th width="100.0155029296875">Type</th><th>Description</th></tr></thead><tbody><tr><td>field</td><td>string</td><td>The name of the field to check</td></tr><tr><td>prefix</td><td>string</td><td>The prefix string to use</td></tr></tbody></table>

***

## RangeQuery <a href="#rangequery" id="rangequery"></a>

`RangeQuery(field, min_value, max_value, lower_inclusive=True, upper_inclusive=False)`\
An Elastic Query DSL [Range Query](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/query-dsl-range-query.html).

<table><thead><tr><th width="206.54534912109375">Name</th><th width="99.764404296875">Type</th><th>Description</th></tr></thead><tbody><tr><td>field</td><td>string</td><td>The name of the field to check</td></tr><tr><td>min_value</td><td>numeric</td><td>The lower bound to match above</td></tr><tr><td>max_value</td><td>numeric</td><td>The upper bound to match below</td></tr><tr><td>lower_inclusive</td><td>boolean</td><td>Include exact matches on the lower bound. Default: True</td></tr><tr><td>upper_inclusive</td><td>boolean</td><td>Include exact matches on the upper bound. Default: False</td></tr></tbody></table>

***

## FuzzyQuery <a href="#fuzzyquery" id="fuzzyquery"></a>

`FuzzyQuery(field, search_t, fuzziness=None, prefix_length=None, max_expansions=None, transpositions=None)`\
An Elastic Query DSL [Fuzzy Query](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/query-dsl-fuzzy-query.html).

<table><thead><tr><th width="206.54534912109375">Name</th><th width="99.764404296875">Type</th><th>Description</th></tr></thead><tbody><tr><td>field</td><td>string</td><td>The name of the field to check</td></tr><tr><td>search_t</td><td>string</td><td>The fuzzy search string</td></tr><tr><td>fuzziness</td><td>integer</td><td>The edit distance to match from. See <a href="https://www.elastic.co/guide/en/elasticsearch/reference/6.8/common-options.html#fuzziness">documentation</a>. Defaults to automatic.</td></tr><tr><td>prefix_length</td><td>integer</td><td>The number of initial characters to not consider part of the fuzzy match. Default: 0</td></tr><tr><td>max_expansions</td><td>integer</td><td>The maximum number of terms that the fuzzy query will expand to. Defaults to 50.</td></tr><tr><td>transpositions</td><td>boolean</td><td>If character transpositions are supported in the match (i.e. ab->ba would have a distance of 1 rather than 2). Default: False</td></tr></tbody></table>

***

## QueryString <a href="#querystring" id="querystring"></a>

`QueryString(query, params=None)`\
An Elasticsearch default [string query](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/query-dsl-query-string-query.html). Supports Lucene syntax.

<table><thead><tr><th width="100.0689697265625">Name</th><th width="100.4501953125">Type</th><th>Description</th></tr></thead><tbody><tr><td>query</td><td>string</td><td>The query string</td></tr><tr><td>params</td><td>dictionary</td><td>Optional – Additional parameters as defined by the <a href="https://www.elastic.co/guide/en/elasticsearch/reference/6.8/query-dsl-query-string-query.html">Elasticsearch documentation</a>.</td></tr></tbody></table>
