## Exploring open data quality: report

This report summarises the results of a short exploratory project to explore the data quality of three UK government open datasets. The project is a joint exercise carried out by the Open Data Institute (ODI) and [the Experian data quality team](https://www.edq.com/uk).

The goals of the project were to:

* Identify the types of data quality issues that might occur in some existing open datasets

* Suggest common data quality checks that both publishers and users can apply to data

* Explore the idea of an "open data quality index", building on the ODI’s existing work on [open data certificates](https://certificates.theodi.org/en/) and [benchmarking open data](https://theodi.org/guides/benchmarking-data-automatically)

A summary of the findings are available below. The data quality summaries produced during the exercise have also been published under an open licence so can be freely accessed, used and shared.

### Methodology

For an initial exploratory analysis two aspects of data quality were investigated: 

1. The quality of the publication of the dataset, i.e. the measures taken to publish and share the data for reuse, and

2. The structure and contents of the datasets

The first aspect was reviewed by looking at the [open data certificates](https://certificates.theodi.org/en/) (or documentation) associated with each dataset.

The second aspect was investigated by using [the Experian Pand](https://www.edq.com/uk/solutions/experian-pandora/)[ora](https://www.edq.com/uk/solutions/experian-pandora/)[ data quality tool](https://www.edq.com/uk/solutions/experian-pandora/) to explore the datasets and generate some high-level data quality reports.

The data to be reviewed were chosen based on the following criteria:

* The data was tabular, so could be processed with Pandora

* The datasets including a mix of data types, including some address data

* The datasets were published by different organisations, to ensure we had a mix of data governance practices

* The datasets were known to be collated using a number of methodologies including public registration (e.g. a Director registering their own business), local expert contributions (e.g. property sales) and central management (e.g. by the NHS)

* The datasets were likely to be relevant in a wide variety of use cases, so any identified improvements would have impact for a number of potential reusers

After an initial review of data.gov.uk, we selected three datasets published by the Land Registry, Companies House and the NHS.

The datasets were then reviewed as follows:

1. Datasets were downloaded as CSV files and imported into the Pandora tool

2. Each dataset was manually reviewed to confirm it had been correctly imported

3. Some exploratory analysis was carried out by using Pandora’s data summarisation tools to gain familiarity with each dataset and the range of data types it contained

4. Two standard reports were generated for each dataset, summarising their structure and contents

5. A third report was also generated, giving an indication of how well the address data in each dataset could be matched against the Royal Mail Postal Address File (PAF) 

6. An attempt was made to find the open data certificate for each dataset by looking at the dataset homepage, it’s entry on data.gov.uk or, as a fallback, by searching within the certificates application. If found, then the certificate was then reviewed

### Reviewed Datasets

The reviews were carried out on the following datasets. 

  

1. Land Registry Price Paid data

    1. [dataset homepage](https://data.gov.uk/dataset/land-registry-monthly-price-paid-data) (specifically: "2015 FULL Price Paid Data-Single file 1995-2015")

    2. [open data certificate](https://certificates.theodi.org/en/datasets/26552/certificate) (silver)

2. The Companies House register

    3. [dataset homepage](http://download.companieshouse.gov.uk/en_output.html) (all data files were downloaded, unzipped and imported)

    4. no open data certificate was found for this dataset

3. The NHS Choices Data Service GP Practices and Surgeries dataset

    5. [dataset homepage](https://data.gov.uk/dataset/gp-practices-and-surgeries)

    6. no open data certificate was found for this dataset

The reviews were carried out on 16th August 2016 using the latest available data on that date.

### Data Quality Reports

Three reports have been generated for each of the datasets. These are:

1. A column summary report that describes the structure of the dataset

2. An outliers report that provides insight into the contents of each column

3. An address matching report that highlights how well the address data can be matched against Royal Mail PAF 

The individual reports are formatted as CSV files. These have been published under a Creative Commons Attribution licence using [octopub](https://octopub.io/). 

The individual data packages can be downloaded using the following links:

1. [Land Registry Price Paid data](https://paulmalyon.github.io/land-registry-price-paid-data-quality/)

2. The [Companies House register](https://paulmalyon.github.io/companies-house-corporate-dataset-column-stats/)

3. The NHS Choices [GP Practices and Surgeries dataset](https://paulmalyon.github.io/gp-practices-and-surgeries-data-quality-overview/)

### Summary: Land Registry

The Land Registry dataset has a self-assessed Silver level open data certificate. While the data is published as both Linked Data and as CSV downloads, only the CSV version was reviewed in this study.

The CSV file: 

* Does not include headers that describe each of the columns

* Is not published with a schema that provides further information about the data

* Has human-readable documentation, which is [separately published on gov.uk](https://www.gov.uk/guidance/about-the-price-paid-data).

Investigating the contents of the data highlighted that:

* There are consistent data types in each column

* The date ranges in the dataset metadata match those given in the transaction date column

* The columns are well-populated and the overall and dominant datatypes match the documentation. Some of the lower completeness scores are to be expected from address variations, e.g. not all addresses have a "Secondary Addressable Object Name". It is notable that there are around 22,000 rows with missing post codes

* The "Duration" column includes a value (“U”) which is not described in the documentation.

* The dataset documentation doesn’t define the meaning of all of the address fields. Inspecting the data shows that contents of the the "County" column are a mix of UK counties and cities

* Attempting to match all of the Registered Office Address fields against PAF shows that a partial match on premises is possible for around 92% of the data, with a good or complete match for around 42% of the records

* A number (around 88,000) of potential duplicate or repeated transactions were also highlighted. These involved multiple transactions for the same property on the same day. The reason for these is unknown but could indicate an historic data collection issue.

In terms of its structure and consistency of content the dataset appears to have a reasonably high quality.

### Review: Companies House

A quick review of the dataset homepage shows that only limited information and metadata is available for reusers:

* There is no open data certificate

* There is no licence describing what rights reusers have over the data

* There is no schema for the dataset

* There is no detailed user documentation for the data, although there is [a list of the column names and their maximum sizes](http://resources.companieshouse.gov.uk/toolsToHelp/pdf/freeDataProductDataset.pdf)

* There is no metadata about the data, just a title and the date of last update

In addition the CSV data has been split into several files that have then been individually zipped. This creates additional work on reusers who have to reassemble the whole data file. In addition, as the individual CSV files include headers, these need to be removed from each individual file before combining them to create the final dataset.

Investigating the contents of the data highlighted that:

* There are a number of columns that are always populated, e.g. company number, status and a SIC code

* There are a number of optional or rarely used columns, e.g. previous company names

* The dataset uses a different set of address fields to that used in the Land Registry dataset. There is a varying degree of completeness for these fields

* Some of the address fields include what appear to be notes rather than actual addresses, e.g. "BRANCH REGISTRATION" and “REFER TO PARENT REGISTRY” both appear in a number of records

* While the completeness of the SIC Code 1 field is 100% indicating that a value is always provided in the data, in a number of cases this value is "NONE SUPPLIED"

* Compared with the Land Registry dataset which has 8 different formats for post codes, the Companies House register has more than 300 formats in the Registered Office Address postcode column. This suggests that the data has not been validated at all and is likely to be based on manual data entry

* Consistent with the above, looking at the minimum and maximum values for the address fields shows examples of invalid or incorrect data

* Attempting to match all of the Registered Office Address fields against PAF shows that a partial match on premises is possible for around 85% of the data, with a good or complete match for around 43% of the records

* There are a number of other data values that look incorrect, e.g. at least one company with a negative number of partnerships, or the company which has an accounts next due date of "01-Nov-1877", etc.

Our understanding is that the data collected and published by Companies House in this version of the register is the raw, manually entered data provided during company registration. As such it demonstrates a much lower quality and consistency that the Land Registry data. 

Matching data against an authoritative address source would significantly improve the quality of the open data.

### Review: NHS GP Practices

The GP Practices and Surgeries dataset is published by NHS Choices. The dataset is aligned with a similar set of data that is provided by the NHS Organisational Data Service but which is published in a slightly different format and to a separate location.

* The original data was published as a file delimited with a "not" (¬) symbol rather than a CSV. The data.gov.uk platform has a version converted to CSV for easier use by standard tools.

* There is no open data certificate for the dataset

* There is no schema for the data

* There is some [documentation for the dataset](http://media.nhschoices.nhs.uk/data/foi/GP.pdf) including a list of columns, their lengths and whether they are mandatory

* The [data.gov.uk entry for the dataset](https://data.gov.uk/dataset/gp-practices-and-surgeries) indicates that is was published in March 2015. However there is [more recent data about GP practices available from the NHS Organisational data service](http://systems.digital.nhs.uk/data/ods/datadownloads/gppractice) so the data may in fact be out of date 

Looking at the content of the dataset:

* Some of the columns contain identical values. For example the Organisation Type is always "GP", Sub Type is always “UNKNOWN” and Organisation Status is “Visible”. These columns are therefore redundant in this dataset as they contain no useful information. The data may be an extract of a larger dataset in which these columns have more useful values

* It is not clear, without further research what the "Is Pims Managed" and “Is EPS Enabled” columns mean. These are both flags that are associated with the practices

* There is another set of Address fields used in this dataset, so no alignment with the other datasets

* The postcode data seems to have been validated as there are only 6 different formats

* Matching against PAF shows that over 90% of the data can have a good premise match, and 36% have a verified or full match

* There are a set of contact fields for the practices, including phone, fax, email address and website. Only 24% of the practices have an email address listed, nearly 50% of the practices have a website, but 98% have a phone number

* Inspecting the contact fields shows some quality errors, for example email addresses or phone numbers in the website column

* For some rows in the dataset, columns have either been transposed or have been accidentally shifted. This may be down to a problem during the conversion between the different delimited file formats on data.gov.uk, or perhaps an encoding problem with the original data

The basic problems with formatting of this dataset make this dataset extremely difficult to use in its current form. A reuser would need to put effort into identifying the source of the problem or in cleaning up the data.

The Organisational Data Service would likely offer a better source of this data, however it is not listed on data.gov.uk and so less discoverable for users.

### Conclusions

This brief survey has highlighted a number of data quality issues with several datasets available on data.gov.uk.

The issues relate to:

* **The quality and effort placed into publishing data**, e.g. ensuring it is well formatted, documented, has a clear licence and is kept up to date

* **Inconsistent approaches towards describing the same data**, e.g. the structure and format of an address

* **Lack of machine-readable schemas** that might be used to validate data both before publication and reuse

* **Inconsistent use of existing authoritative sources**, e.g. address registers to improve the quality of data

An open address register would have obvious benefits in improving data quality across all of these datasets. The ability to link to authoritative data could also potentially reduce the amount of data that would need to be published. The data files could simply include a unique address identifier that would allow reusers to lookup the authoritative data in a consistent format.

Exploring the data with a dedicated data quality tool made it easier and quicker to identify and highlight potential problems. The ability to see a summary of the dataset structure and the range of column values provided immediate insight into both the contents of the dataset and potential quality issues.

It’s clear that there are opportunities for the open data community to invest further effort in data quality analysis and reporting tools that could help improve the data quality of existing datasets. Running these metrics on a regular basis against key datasets could provide a useful resource for the whole community.

