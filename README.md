# justqueryme
Query your database in plain language using Artificial Intelligence

## Synopsis

Engine that will parse natural language queries and translate them to specific datasource query formats (SQL, Json, etc)

## Motivation

Natural Language Processing (NLP) has advanced a lot in recent years. However, we still lack a simple open source way for humans to query datasources without having to understand specific query formats and database nuances. Wouldn't it be better to ask:

"Tell me my total in sales this month"

Instead of

SELECT SUM(SALES) FROM SALES WHERE SALES_DATE BETWEEN ... AND ... GROUP BY ...

## A VERY simple idea of architecture until we have more time to do the "real thing"

- NLP Processor
Current plans involve using google's SyntaxNet (https://github.com/tensorflow/models/tree/master/syntaxnet) to parse the POS tags. 

- Datasource Semantic Parser
Will contain a representation of each datasource element mapped to POS tags:
  - Sources - (e.g. Datasource SALES will be mapped to "sales", "total sales", "customer purchases", etc
  - Filter -  "this month", "this year", "less than", "no bigger than"
  - Groups - "grouped", "organized by", "separated by", "clustered by", etc
  - Calculations - "in percentages", "in 1000s", "whole numbers"
  - etc...
  
Once tags are associated with the query elements, the parser will build a datasource agnostic representation of the query.

- Datasource Driver
Every "query type" (SQL, Json), will have a driver associated with it. This driver is responsible for translating the query agnostic representation into an actual query request which can then be passed to the datasource.

## Some general idea of the potential capabilities

- Not only parse the request but the return agnostic query representation would contain a list of further questions that can be asked of the user (or defaulted to specific values) to make the query more relevant.
- Ability to recognize a certain level of mispelling
- Engine would return a natural language description of the request "in its own language". This can optionally be displayed to the user to ensure accuracy and understanding.
- Learning of the user preferences in querying, filtering, etc, so defaults in the future can be more specific to the user's behavior and past queries.
- Integration with Google home and Alexa...

## Project Status

This project has JUST started. We are still building the basic architecture and will have more information in the future. However, we welcome any AI/Machine Learning/NLP/Other enthusiasts who find this interesting to join us. Not quite sure? No problem, just watch us for a while. More content to come!

## License

Apache 2.0
