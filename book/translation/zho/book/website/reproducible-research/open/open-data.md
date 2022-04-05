(rr-open-data)=
# Open Data

The world is witnessing a significant global transformation, facilitated by technology and digital media, and fuelled by data and information. This transformation has enormous potential to foster more transparent, accountable, efficient, responsive, and effective research. Only a very small proportion of the original data is published in conventional journals. Despite existing policies on archiving data, in today’s practice data are primarily stored in private files, not in secure institutional repositories, and effectively are lost to the public (and often even to the researcher who generated the data).

This lack of data sharing is an obstacle to international research (be it academic, governmental, or commercial) for two main reasons:

1. It is generally difficult or impossible to reproduce a study without the original data.
2. The data cannot be reused or incorporated into new work by other researchers if they cannot obtain access to it.

Accordingly, there is an ongoing global data revolution that seeks to advance collaboration and the creation and expansion of effective, efficient research programs. Open data [{term}`def<Open data>`] is crucial to meeting these objectives. Open data is freely available on the internet. Any user is permitted to download, copy, analyse, re-process, and re-use it for any other purpose with minimal financial, legal, and technical barriers.

This represents a real shift in how research works. Funders are starting to require researchers to make their data available and submit data management plans {ref}`Data Management Plans<rr-rdm-dmp>` as part of project proposals. At the moment, anyone who wishes to use data from a researcher often has to contact that researcher and make a request. "Open by default" remedies this with a presumption of publication for all. If access to data is restricted, for instance, due to security reasons, the justification for this should be made clear. Free access to and subsequent use of data is of significant value to society and the economy. That data should, therefore, be open by default and only as closed as necessary.

您可以在描述 {ref}的章节中找到更多关于您数据的实际步骤。 `分享您数据的步骤 <rr-rdm-sharing-steps>` 在子章节中： {ref}`分享和归档数据<rr-rdm-sharing>`

(rr-open-data-barriers)=
## Barriers to Data Sharing
Many academics find sharing data difficult. Recent surveys {cite:ps}`Stuart2018sharing` conducted amongst researchers list the following reasons:

- Organising data in a presentable and useful way is challenging (mentioned by 46%)
- Researchers are unsure about copyright and licensing (mentioned by 37%)
- Researchers do not know which repository to use for different data types (raised by 33%)

These are cultural challenges that might be addressed in changing practice going forward. However, there are also legal, ethical or contractual reasons that sometimes prevent making data publicly available in its entirety or even in parts. Below, we discuss some reasons explaining why this may be the case.

```{figure} ../../figures/data-privacy.jpg
---
height: 500px
name: data-privacy
alt: An image detailing why private data should be used. A person stands next to a well with 'private data' written on it and a padlock around it. It is black and white and blue. The text lists that 'people deserve - dignity, agency, privacy, rights, confirmed consent.'
---
_The Turing Way_ project illustration by Scriberia. Original version on Zenodo. [http://doi.org/10.5281/zenodo.3695300](http://doi.org/10.5281/zenodo.3695300)
```

(rr-open-data-barriers-privacy)=
### Privacy And Data Protection

Many fields of research involve working with sensitive personal data, with medical research being the most obvious example. Individuals must be protected from (re)identification via their data used for research. Anonymisation of the data may be sufficient in some cases, but ensuring that (re)identification is not possible is becoming increasingly difficult due to technical progress, growing computational power, and – ironically – more open data. For example, (re)identification may be possible via data-mining of accessible data and so-called quasi-identifiers, a set of (common) properties that are – in their combination – so specific that they can be used to identify individuals.

如果提供了部分或普遍化的数据集，则仍有可能保持隐私。 例如年龄组而不是出生日期，或者只有头两位邮政编码。 还可以用研究人员在关闭数据本身的同时能够查询的格式提供数据。 For example, a user may be able to send a query to retrieve the mean of a dataset, but not be able to access any of the individual data points.

Many fields of scientific disciplines involve working with sensitive personal data. Their management is well regulated in data protection legislation (in Europe through national implementations of the General Data Protection Regulation) and ethics procedures as they are established in most research institutions {cite:ps}`EU2016protection`.

(rr-open-data-barriers-consent)=
### Consent

For anonymised research data to be made available for future reuse, consent forms must cover sharing this data with other researchers. Research so far suggests that study participants are usually less concerned about the data being archived and shared than researchers think {cite:ps}`Kuula2010archiving`. Participant information sheets and consent forms should include how research data will be stored, preserved and used in the long term, and how confidentiality will be protected when needed.

(rr-open-data-barriers-anonymisation)=
### Anonymisation

必须通过其数据保护个人不被（重新）识别。 在某些情况下，数据的匿名化可能就足够了。 但确保不可能重新查验身份正变得越来越困难。 It might even be impossible due to technical progress, growing computational power and – ironically – more open data.

如果提供部分或普遍化的数据集，则仍有可能保持隐私。 例如，您可以提供年龄段而不是出生日期，或者只提供头两位邮政编码。 还可以以研究人员在关闭数据本身的同时能够查询的格式提供数据。 For example, a user may be able to send a query to retrieve the mean of a dataset, but not be able to access any of the individual data points. 但不能访问任何单独的数据点。

(rr-open-data-barriers-national)=
### National and Commercially Sensitive Data

In many cases, companies are understandably unwilling to publish much of their data. The reasoning goes that if commercially sensitive information of a company is disclosed, it will damage the company’s commercial interests and undermine competitiveness. This is based on the thinking that in competitive markets, innovation will only occur with some protection of information. If a company spends time and money developing something new, the details of which are then made public, then its competitors can easily copy it without having to invest the same resources. The result is that no one would innovate in the first place. Similarly, for public safety concerns, governments are often unwilling to publish data that relates to issues such as national security. In such cases, it may not be possible to make data open, or it may only be possible to share partial/obscured datasets.

***Chapter Tags**: This chapter is curated for the `Turing Data Study Group` (`turing-dsg`).*
