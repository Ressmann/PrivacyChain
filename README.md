# Introduction

The PrivacyChain is a distributed, blockchain platform , based on a shared, immutable, distributed ledger. This ledger ensures that participants in a PrivacyChain have a single, consistent, up-to-date view to a consumers opt-ins or opt-outs, something that is more difficult to accomplish with traditional technologies. As a result, PrivacyChain helps publishers and advertisers build more trusting relationships with their customers.  It also provides companies with a standardized consent management solution which speeds and simplifies deployment for all their partners in the data supply chain.  And because of this consistency and ease of deployment, PrivacyChain simplifies companies' ability to prove that they are complying with numerous consumer privacy regulations worldwide, including the California Consumer Privacy Act, General Data Protection Regulation, and the European Privacy Directive, as well as a company's own privacy policies.

A demo is available at http://tools.iabtechlab.com.  Companies interested in testing the specification can build applications that make calls into the testbed and see how they are handled and propagated across the blockchain in a standard implementation.

## Entities
Following entities are defined in privacychain:
1. Data Collector – For example, Brand, Publisher, Data Source of consumer data
2. Data Buyer – For example, Brand, Ad Agency, Data Aggregator
3. Advertiser – For example, Brand, Ad Agency
4. Individual – Consumer, user

## Use Case 1 – Consent Collection

| Title | Data Collector captures consent when an individual's personal data and opt-in preference is being collected |
| --- | --- |
| Description |
1.Individual signs up as a member at the data collector1 ("entity") website
2. Website displays privacy messaging and prompts user to opt-in to accept privacy terms and condition
3. The website requests user to provide consent on the use of the individuals data for these purposes:
  * For the entity to provide basic services
  * For first party site personalization
  * For first party marketing purpose
  * For sharing with third party for market purpose|
| Post condition | Individuals consent along with its meta data2 is captured in PrivacyChain |

## Use Case 2 – Data Movement Tracking

| Title | Advertiser tracks audience data movement when personal data is transferred to a third party   |
| --- | --- |
| Description |
1. Advertiser creates audience segment for advertising campaign
2. Advertiser ensure that audience has provided consent for their data to be used for marketing purpose
3.Advertiser transfers audience segment to third party3 for campaign execution
4. Third party received audience segment |
| Post condition | Transfer of individual's consent along with its meta data4 to the third party is captured in PrivacyChain- Third party receipt of individual's consent along with its meta data is captured in PrivacyChain|

## Use Case 3 – Data Movement Tracking

| Title | Third party tracks audience data movement when data is transferred to another third party. All third parties delete audience data post campaign |
| --- | --- |
| Description |
1.Third party transfers audience segment to another third party5 for campaign execution
2. Third party received audience segment
3. All third parties delete audience data post campaign |
| Post condition | Transfer of individual's consent along with its meta data6 to the third party is captured in PrivacyChain - Third party receipt of data and individual's consent along with its meta data is captured in PrivacyChain
- Third parties deletion of individual&#39;s data post campaign is captured in PrivacyChain|

## Use Case 4 – Consent Collection

| Title | Data Seller captures individual's consent when individual's personal data is being collected   |
| --- | --- |
| Description |
1.Individual signs up to use services at a data collector7 ('entity') site
2. Website displays privacy messaging and prompts individual to opt-in to accept privacy terms and condition
3. Privacy terms and condition and opt-in include individual personal data collection:
  * For the entity to provide basic services
  * For first party site personalization
  * For first party to share data with third party part of data sales|
| Post condition | Individual's consent along with its meta data8 is captured in PrivacyChain |

## Use Case 5 – Data Movement Tracking

| Title | Data Seller tracks data movement when individual's data is sold and transferred to third party   |
| --- | --- |
| Description |
1.Data Seller sold opt-in individual data to a third party9
2. Third party received data from Data Seller |
| Post condition | Transfer of the individual's consent along with its meta data10 to the third party is captured in PrivacyChain. Third party receipt of data and individual's consent along with its meta data is captured in PrivacyChain|

## Use Case 6 – Individual Inquiry

| Title | Individual inquires consent status and data movement |
| --- | --- |
| Description |
1. User login to brand website he/she signed up previously
2. User inquires attribute(s) he/she has provided data to the brand
3. User inquires movement of his/her data outside of the brand |
| Post condition | The brand's website displays a list of user's attribute(s) along with meta data:
   * Consent status
   * Expiry date
   * Usage/purpose
   * The brand's website displays a list of third party destinations in which user's data has been shared with/transferred to |

## Use Case 7 – Data Propagation

| Title | Individual manages his/her consent and updated consent propagates to downstream entities |
| --- | --- |
| Description |
1. User login to brand website he/she signed up previously
2. User inquires attribute(s) he/she has provided data to the brand
3. User revoke consent to share data with third party |
| Post condition |
 * The action of revoking consent to share data with third party is captured in PrivacyChain
 * PrivacyChain triggers consent revocation notification to all third-party entities that had received the individual's consent previously |

## Use Case 8 – Auditing

| Title | Regulator auditing Data Collector and Data Processor's privacy practice |
| --- | --- |
| Description |
1. Regulator access PrivacyChain
2. Regulator retrieve audit trail of data collection, data movement with consent along with the metadata for a particular Data Collector/Processor|
| Post condition |
 * PrivacyChain supports audit trail data extraction
 * Regulator determines compliance |

## Use Case 9 – External Governance and Monitoring

| Title | Regulatory authority and consumer advocacy group monitors the integrity of the consortium |
| --- | --- |
| Description |
1. Regulatory authority and consumer advocacy group request setting up and running PrivacyChain nodes
2. PrivacyChain consortium approves request via PrivacyChain governance process
3. Regulatory authority and consumer advocacy group follow provisioning instructions
4. PrivacyChain provision regulatory authority and consumer advocacy group within the network |
| Post condition |
 * Regulatory authority and consumer advocacy group each runs a node within PrivacyChain
 * Regulatory authority and consumer advocacy group access data within the ledger |

## API Calls

API specification can be found in Swaggerhub repository
https://app.swaggerhub.com/apis/jhsy/PrivacyChain/1.0.0#/](https://app.swaggerhub.com/apis/jhsy/PrivacyChain/1.0.0#/

| **Item #** | **Priority** | **Endpoint** | **Parameters** | **Method** | **Notes** |
| --- | --- | --- | --- | --- | --- |
| CT-01 | MVP | /consent | {id}{consentType}{entity}{expires}{attributes}{status} | POSTPUT | Add a new consent record to the chainUpdate an existing consent |
| CT-02 | V1.0 | /consent/createWithArray | {id}{consentType}{entity}{expires}{attributes}{status} | POST | Create multiple consents with given input array |
| CT-03 | V1.0 | /consent/createWithList | {id}{consentType}{entity}{expires}{attributes}{status} | POST | Create multiple consents with input list |
| CT-04 | MVP | /consent/findIdsByEntity |   | GET | Find consent IDs by entity |
| CT-05 | MVP | /consent/{consentId} | {id}{consentType}{entity}{expires}{attributes}{status} | GET | Find consent by consent ID |
| CT-06 | V1.0 | /consent/revokeWithArray |   | POST | Revoke multiple consent records |
| CT-07 | MVP | /consent/revoke/{consentId} |   | POST | Revoke single consent record |
| DT-01 | MVP | /datatransfer | {id}{consentId}{source}{destination}{attributes}{status} | POSTPUT | Log data transfer actionUpdate an existing data transfer |
| DT-02 | V1.0 | /datatransfer/createWithArray | {id}{consentId}{source}{destination}{attributes}{status} | POST | Create data transfers with given input array |
| DT-03 | V1.0 | /datatransfer/createWithList | {id}{consentId}{source}{destination}{attributes}{status} | POST | Create data transfer with given input list |
| DT-04 | MVP | /datatransfer/findByConsentID | {id}{consentId}{source}{destination}{attributes}{status} | GET | Find data transfers by consent ID |
| DT-05 | MVP | /datatransfer/{datatransferId} | {id}{consentId}{source}{destination}{attributes}{status} | GET | Find data transfer by data transfer ID |
| SB-01 | V1.0 | /subscription | {id}{consentId}{entity}{subscriptionDate}{email}{status} | POST | Subscribe to notifications for all events related to a consent record |
| SB-02 | V1.0 | /subscription/findByEntity |   | GET | Return subscriptions for an entity |
| SB-03 | V1.0 | /subscription/{subscriptionId} |   | GETDELETE | Find subscription by subscription IDDelete subscription by subscription ID |
