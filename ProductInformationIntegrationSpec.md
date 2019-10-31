# Product Information Ingestion Library

## Overview

Swiftly needs to integrate with a grocery store's product information system so our system can stay current with the store's product inventory and pricing.

![Product Information Integration Architecture](https://github.com/prestoqinc/code-exercise-services/raw/master/Swiftly_Services_Coding_Exercise_Architecture.png "Product Information Integration Architecture")

## Requirements
Each store has its own product catalog service
* Changes to product information are published to our integration service using a fixed-width flat file format defined by the store’s point of sale system (specifications below)
* The store publishes update journal files at most every 60 seconds

*Input*: Store product catalog information<sup>[1](#footnote1)</sup>.  You can assume that this is a formal API contract that has zero bugs and will never change.

*Output*: A collection of _ProductRecord_ objects<sup>[2](#footnote2)</sup>

## Input Data Format
The file is in an ASCII-encoded flat file (fixed width) format with the following layout:

| Start | End [Inclusive] | Name                       | Type     |
|-------|-----------------|----------------------------|----------|
| 1     | 8               | Product ID                 | Number   |
| 10    | 68              | Product Description        | String   |
| 70    | 77              | Regular Singular Price     | Currency |
| 79    | 86              | Promotional Singular Price | Currency |
| 88    | 95              | Regular Split Price        | Currency |
| 97    | 104             | Promotional Split Price    | Currency |
| 106   | 113             | Regular For X              | Number   |
| 115   | 122             | Promotional For X          | Number   |
| 124   | 132             | Flags                      | Flags    |
| 134   | 142             | Product Size               | String   |

### Field Data Types
* Number - an integer value 8-digits long, zero left-padded
* String - ASCII encoded string, space right-or-left-padded
* Currency - US dollar value, where last two digits represent cents.  The leading zero will be replaced with a dash if the value is negative
* Flag - Y/N

### Pricing Information
* Prices can either be a singular price per unit (e.g. $1.00) or a split price (e.g. 2 for $0.99).  Only one price per pricing level will exist.  The other will be all 0's, which indicates there is no price.
* If a price is split pricing, the Calculator Price is Split Price / For X
* You can be guaranteed that the input file will follow these rules – consider it a contract that the producer will always abide by.  No error checking is required for this first stage.

### Flags
The first flag in the left-to-right array is #1
* If Flag #3 is set, this is a per-weight item
* If Flag #5 is set, the item is taxable.  Tax rate is always 7.775%

## ProductRecord object should contain at a minimum:
* Product ID
* Product Description
* Regular Display Price (English-readable string)
* Regular Calculator Price (price the calculator should use, rounded to 4 decimal places, half-down)
* Promotional Display Price, if it exists
* Promotional Calculator Price, if it exists
* Unit of Measure ("Each" or "Pound").  Weighted items are per pound
* Product size
* Tax rate

______________________________________________________________________________________________________
<sup><a name="footnote1">1</a></sup> An [example file](../master/input-sample.txt) is included in the GitHub repository for the coding exercise.

<sup><a name="footnote2">2</a></sup> This object will be used to update the database, but updating the database isn't part of this exercise
