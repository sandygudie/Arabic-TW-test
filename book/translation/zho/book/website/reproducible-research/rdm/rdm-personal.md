(rr-rdm-personal)=

## Personal data management
This section provides a general overview of things to consider when working with personal data. For a more practical overview on tools and practises that facilitate reproducibility, please see the {ref}`Sensitive Data Projects<pd-sdp>` chapter.

### Personal data

个人数据是关于 **个活人** 的信息，他们可以使用您正在处理的数据进行识别。 直接或间接（例如一个人的姓名、地址或其他独特的身份识别特征，例如他们的社会保障号码）。 [与死者有关的数据在大多数情况下不被视为GDRPR](https://gdpr.eu/eu-gdpr-personal-data/) 之下的个人数据。" 间接识别资料包括健康、经济、文化或社会特征。 Especially when a certain combination of these identifiers can be used to identify a person, care must be taken to manage the data properly. Particularly sensitive data include data relating to a person's:
* racial/ethnic identity
* political opinions
* religious/philosophical beliefs
* trade union membership
* genetic and biometric data
* physical or mental health
* sexual orientation

### Personal data policies
There are various policies in place in different countries to protect the rights of individuals over their personal data. For example, in Australia personal data is regulated under the [Australian Privacy Act](https://www.oaic.gov.au/privacy/the-privacy-act/). In the European Union the **GDPR** (General Data Protection Regulation) applies to the processing of personal data and may require you to carry out a Data Protection Impact Assessment ([DPIA](https://youtu.be/YRiCb3unz3g?t=988)). Processing means doing anything with a person's information, including collection, storage, analysis, sharing, deletion and destruction. To ensure that you are up to date with the requirements of managing sensitive data, please review the national/institutional policies that apply to your research. See {cite}`Smith2015participantdata` for recommended practices for sharing clinical trial data.


(rr-rdm-informed-consent)=

### Informed consent

Informed, voluntary and fair consent to participate in a study is very important for any research project that involves human participants. It is through this consent process that research participants can understand what taking part in a specific study will mean for them. Each person can then choose whether to participate using the consent form. See also the {ref}`Guide for Ethical Research<er>`.

Note that the informed consent form is considered to be personal data and should therefore be handled with the same care as other personal data. Do not store the consent forms where you store the rest of the data you collect; use a separate locked cabinet or an encrypted folder for example.

In case you cannot use a written consent form, try to make a recording of verbal consent.

**Consent documentation should include:**

* a participant information sheet and

* a consent form signed by the participant.

The **participant information sheet** is used to inform participants about the study. The information should be clear and easy to understand and should cover the following:
* What the project is about.
* What their participation will involve.
* Any risks involved for participants and safeguards to minimise those risks.
* Assurances about data security and participant confidentiality.
   * Mention who has access to the data
* How the data will be used in the study (for published articles, reports and presentations).
* Proposed plans for archiving data at the end of the study and potential future secondary re-use of data.
    * Tiered consent may be a solution here, by allowing the participants to choose what type of information will be shared publicly
* Details of the organisation overseeing the research.
* Whom to contact for more information about the study.

The **consent form** is used to verify that the research participant understands and agrees to participate in the study. The consent form should cover the following points at a minimum:
* The participant
    * has read and understood the participant information sheet
    * has been given the opportunity to ask questions
    * understands that participation is voluntarily
    * understands that they may withdraw from the study at any time without giving reasons and without penalty
    * understands how the data will be managed, shared and archived (as detailed in the information sheet)
       * to increase the chance of your data to be reused, do not promise to delete the data but instead ask for consent to retain and share the data (see {cite}`Meyer2018personaldata`)
* Signatures of both the participant and the researcher, and the date of signing

Think ahead and plan how you will:

* collect, store and manage the data (see {ref}`Data storage and organisation<rr-rdm-storage>`)

* control access permissions

* prepare data for archiving/sharing at the end of the project if possible (see {ref}`Sharing and archiving data<rr-rdm-sharing>`)


(rr-rdm-privacy)=

There are a number of strategies that you can adopt to **safeguard the privacy** of your research subjects:

**1. 1. 最大限度地减少数据**

* If personal information isn't needed, don't collect it.
* Periodically review whether you are retaining unnecessary identifying information.
* When identifying information is no longer needed, safely remove, delete or destroy it.

**2. 2. 数据保留限制**
* Decide how long you will retain identifiable data before removing direct identifiers, applying more complex anonymisation techniques, or deleting the data altogether.
* When deleting sensitive data you need to be aware that standard methods for deleting files (for example moving files to the recycle bin and emptying it) are not secure. These deleted files may be recovered. Use software like BleachBit to safely delete the data.

**3. 3. 安全数据传输**
* Before deciding to transfer personal data, you should consider whether the transfer of identifiable data is necessary. For example, can data be de-identified or anonymised?
* If data cannot be made unidentifiable then you must ensure you have authority to transfer the personal data, and that there are appropriate safeguards in place to protect the data before, during and after transit.
* Often your university or institute will provide solutions for secure file transfer. Contact you research data, privacy or IT support team for guidance.

**4. Encryption**
* Encryption provides protection by ensuring that only someone with the relevant encryption key (or password) will be able to access the contents.
    * Protect on disk level: Bitlocker for Windows, FileVault for MacOS
    * Protect on “container” level (a folder containing multiple files):  Veracrypt (or Archive for MacOS)
    * Portable storage: Bitlocker
    * File level / Exchange information:
      * Simple method: use 7zip, and pack with a password
      * More complicated to setup: use PGP tooling (can also be used to securely send email)
    * See the [Ghent University Encryption for Researchers manual](https://osf.io/nx8km/) for more details and step-by-step guides

**5. 5. 访问权限**
* Management of shared folder permissions.
* Password protection.


**6. Anonymisation**

Anonymisation is a process by which identifying information in a dataset is removed. It is used primarily to allow data to be shared or published without revealing the confidential information it contains, while limiting the loss of information.
* Where possible, direct identifiers (such as names, addresses, telephone numbers and account numbers) should be removed as soon as the identifying information is no longer needed. You can delete the data or replace it with pseudonyms. For qualitative data you should replace or generalise identifying characteristics when transcribing interviews.
* De-identified data that can be re-identified using a linkage file (for example, information linking data subjects to identifiable individuals) is known as pseudonymised data. NOTE: In this instance, the linkage file should be encrypted and stored securely and separately from the de-identified research data.
  * Identification of individuals in pseudonymised or de-identified data may still be possible using combinations of indirect identifiers (such as age, education, employment, geographic area and medical conditions). Further, data and outputs containing small cell counts may be potentially disclosive, particularly where samples are drawn from small populations or include cases with extreme values or relatively rare characteristics.
   * As such, when intending to share potentially identifiable data or the outputs generated from the data, you may need to consider more advanced anonymisation techniques such as statistical disclosure control (SDC, see [this handbook](https://securedatagroup.org/sdc-handbook/) for more information).
* For more information about anonymisation you can watch [this webinar by Enrico Glerean](https://www.youtube.com/watch?v=ILXeA4fx3cI).

**7. 7. 共享敏感数据**

If you plan to share or publish your data you must ensure that your data are appropriate and safe to share. For example, you should consider whether the data can be adequately anonymised, and whether anonymised data will remain useful (see also {ref}`Barriers to data sharing<rr-rdm-sharing>`Open Research Chapter). After applying methods to de-identify and anonymise sensitive data, there may still be a risk of re-identification (see {cite}`Meyer2018personaldata`).

An additional safety measure, or alternative to anonimisation, is applying access controls to ensure the data are shared appropriately and securely. This may involve finding a data repository which can provide suitable access controls (see [here](https://osf.io/tvyxz/wiki/8.%20Approved%20Protected%20Access%20Repositories/) for a list of protected Access Repositories). 这些仓库可以提供对项目元数据的访问，这些元数据允许他人查找， {ref}`引述数据<cm-citable-cite>` 限制访问/条件访问还为潜在的重新用户提供他们访问数据所需的信息，使数据 {ref}`FAIR <rr-rdm-fair>` 例如，获取数据的条件可能要求潜在数据重新使用者： These repositories can provide access to the metadata of the project, which allows others to find and {ref}`cite the data<cm-citable-cite>`. Restricted/conditional access also provides potential re-users with the information they need to access the data, making the data {ref}`FAIR <rr-rdm-fair>`. For example, conditions to access the data could require the potential data re-user to:
  * Register and/or provide contact details to ensure reusers are genuine and aware of their responsibilities
  * Provide information about how they use the data
  * Agree to conditions (data security, privacy, restrictions included in consent forms)

**Resources**
* [Protecting sensitive data course](https://mantra.edina.ac.uk/protectionrightsandaccess) by [MANTRA](https://mantra.edina.ac.uk)
* {cite}`Meyer2018personaldata`.
* [由 \[Zosia Beckles 介绍\](https://youtu.be/J9kWkzK83i4)](https://www.youtube.com/watch?v=J9kWkzK83i4&list=PLyeHH3bEQqIbgbw75gheV27nFF2ctPPpR&index=1), [Michele Voznick](https://youtu.be/w5v5d6r6irs) and [Tessa Darbyshire](https://youtu.be/jEFu1ykVI_I) on Responsible Data Management: Legal & Ethical Aspects as part of the [Fail it session](https://www.youtube.com/c/AI4ScientificDiscovery).
* [Presentation](https://www.youtube.com/watch?v=H2mv6q4WwOU&) by Rob Gommans on GDPR and the Processing of (Identifiable) Image, Audio, and Video Data for Scientific Research Purposes.
* [Presentation](https://youtu.be/_3bufely0c0) by Stephan Heunis on Brain research data and personal data privacy: practical tips to share and protect.
* [Presentation](https://youtu.be/eAKhI0qde2w?t=1104) by Walter Scholger on the GDPR with resources such as informed consent templates (18:30 - 38:50).
* [Presentation](https://www.youtube.com/watch?v=PSe2V1KTQ8w&) on handling personal data by Enrico Glerean and Päivi Lindström from Aalto University. See [here](https://www.aalto.fi/en/services/rdm-training) for the full course.
* 由Rosalie Salameh 在GDRPR上演示
* [Presentation](https://vimeo.com/362161972) and [article](https://www.smashingmagazine.com/2017/07/privacy-by-design-framework/) on **privacy by design**.
* 关于Hina Zahid分享数据中的伦理和法律问题的介绍
* [Slides](https://osf.io/5xhya/) by Hanne Elsen on Privacy and the GDPR in the Research Life Cycle.
* [Workshop materials](https://osf.io/em3da/) on data de-identification procedures for data sharing.
