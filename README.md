# `ToTA`: Texts of Trade Agreements

<img align="center" src="http://mappinginvestmenttreaties.com/rta/assets/img/github_tota_title_image.png">


`ToTA` is a machine-readable and annotated full text corpus of preferential trade agreements (PTAs) in XML format.

`Version 0.5.0`

# Context

The number of trade agreements has dramatically increased since the early 1990s. Trade agreements cover ever more issues and an average agreement text is now around ten times longer than 25 years ago. This makes it more and more difficult to analyze the content of trade agreements and assess their impact on international trade and welfare. Big data and text-as-data methods can help researchers, policy-makers and other stakeholders to better manage the growing complexity of trade agreements.

# Need for digitized texts

Modern computational methods, however, require the existence of machine-readable texts. While several databases make PTA texts available, they are generally optimized for reading, but not computational analysis. As part of a year-long effort, this project used the WTO RTA Database to locate text and meta-data of close to 450 preferential trade agreements and transformed them into a machine-readable format that allows analysis on the article, chapter or treaty-level of PTA texts.

# Corpus description

This corpus builds on the [WTO Regional Trade Agreements Information System](http://rtais.wto.org) data. We gather metadata and full texts from this source, correct the deficiencies (missing full texts or incorrect metadata), apply optical character recognition or other methods to arrive at machine-readable texts, remove annexes or schedules, impose two-level hierarchy of treaty elements, and, finally, produce XMLs that are stored in `xml/` folder. Please note that the texts may contain errors due to optical character recognition deficiencies.

## Structure

XML structure is as follows (example is for [xml/pta_442.xml](https://github.com/mappingtreaties/tota/xml/pta_442.xml)):

```xml
<treaty>
  <meta> <!-- Metadata fields that build on WTO RTAIS cards, e.g. http://rtais.wto.org/UI/PublicShowRTAIDCard.aspx?rtaid=911 -->
    <name>Canada - Honduras</name> <!-- "Agreement name" from WTO RTA card -->
    <type>Free Trade Agreement &amp; Economic Integration Agreement</type> <!-- "Type" from WTO RTA card -->
    <wto_rta_id>911</wto_rta_id><!-- "rtaid" treaty identifier from WTO RTA card (in URL) -->
    <treaty_identifier>442</treaty_identifier> <!-- ToTA treaty identifier. This identifier is in XML file name -->
    <status>In Force</status> <!-- "Status" from WTO RTA card -->
    <notification>GATT Art. XXIV &amp; GATS Art. V</notification> <!-- "Notification under" from WTO RTA card -->
    <date_signed>2013-11-05</date_signed> <!-- "Date of signature" from WTO RTA card -->
    <date_into_force>2014-10-01</date_into_force> <!-- "Date of entry into force" from WTO RTA card -->
    <date_notification>2015-02-05</date_notification> <!-- "Date of notification" from WTO RTA card -->
    <end_implementation>2028-12-30</end_implementation> <!-- "End of implementation period" from WTO RTA card -->
    <date_inactive/> <!-- "Date inactive" from WTO RTA card -->
    <parties_original> <!-- "Original signatories" from WTO RTA card with country names converted to ISO 3166-1 alpha-3 codes. -->
      <partyisocode n="1">CAN</partyisocode>
      <partyisocode n="2">HND</partyisocode>
    </parties_original>
    <parties> <!-- "Current signatories" from WTO RTA card with country names converted to ISO 3166-1 alpha-3 codes. -->
      <partyisocode n="1">CAN</partyisocode>
      <partyisocode n="2">HND</partyisocode>
    </parties>
    <composition>Bilateral</composition> <!-- "RTA Composition" from WTO RTA card -->
    <region>North America; Central America</region> <!-- "Region" from WTO RTA card -->
    <parties_wto>Yes</parties_wto> <!-- "All Parties WTO members?" from WTO RTA card -->
    <crossregional>Yes</crossregional> <!-- "Cross-Regional" from WTO RTA card -->
    <language>en</language> <!-- Language of treaty full text -->
    <!-- Information on treaty sources (for full text and annexes) -->
    <source lang="en" type="full text">http://www.international.gc.ca/trade-agreements-accords-commerciaux/agr-acc/honduras/toc-tdm.aspx?lang=eng'</source>
    <source lang="es" type="full text">http://www.prohonduras.hn/dgiepc/texto-normativo-9.html'</source>
    <source lang="fr" type="full text">http://www.international.gc.ca/trade-agreements-accords-commerciaux/agr-acc/honduras/toc-tdm.aspx?lang=fra'</source>
    <source lang="en" type="annex">http://www.international.gc.ca/trade-agreements-accords-commerciaux/agr-acc/honduras/toc-tdm.aspx?lang=eng'</source>
    <source lang="es" type="annex">http://www.prohonduras.hn/dgiepc/texto-normativo-9.html'</source>
    <source lang="es" type="annex">http://www.international.gc.ca/trade-agreements-accords-commerciaux/agr-acc/honduras/toc-tdm.aspx?lang=fra'</source>
  </meta>
  <body> <!-- Treaty full text (without annexes or schedules)
              Every treaty has chapter → article structure.
              Preambles/Concluding statements are treated as chapters with name "Preamble" or "Conclusion" -->
    <chapter name="Preamble" chapter_identifier="4527"> <!-- chapter_identifier is unique chapter ID -->
      <!-- Note that each article has its own unique identifier.
           Also note that we respect newline formatting of original documents. -->
      <article article_identifier="39135">PreambleCanada and the Republic of
    Honduras (“Honduras”), hereinafter referred to as “the
    Parties”, resolved to:
      ...
      </article>
      ...
    </chapter>
  </body>
</treaty>
```

The resulting data contains 448 PTA texts notified to the WTO, and two texts for Trans-Pacific Partnership agreement (in English and Spanish). When the PTA texts are available in more than one of the official WTO languages (English, French, Spanish) we prioritise English and report the respective XML in this language.

# Approach and Findings

Based on the `ToTA` infrastructure, one could employ text-as-data methods to automatically map the content of PTAs gaining new insights on trade agreements. Textual similarity measures, for example, are able to capture fine-grained differences in treaty design. So-called dimensionality reduction techniques, which compress the textual information contained in a text into a set of abstract variables, help predict trade flows more accurately than previously available measures.

# Authors

Wolfang Alschner (University of Ottawa), Julia Seiermann (UNCTAD & IHEID), Dmitriy Skougarevskiy (European University at St. Petersburg & IHEID).

# Citation

Wolfgang Alschner, Julia Seiermann & Dmitriy Skougarevskiy (2017): Text-as-data analysis of preferential trade agreements: Mapping the PTA landscape, UNCTAD Research Paper No. 5, UNCTAD/SER.RP/2017/5.

# Acknowledgments

We thank Veronika Zhirnova and Kseniia Tumasova for research assistance and gratefully acknowledge the funding support of the SNSF project “Convergence versus divergence? Text-as-data and Network Analysis of International Economic Law Treaties and Tribunals” (grant `162379`) and UNCTAD. 

# Contact

Dmitriy Skougarevskiy ([@memoryfull](https://github.com/memoryfull)).

# Disclaimer

This data may contain errors due to, amongst others, mistakes in the source data, errors induced by the OCR conversion or the manual mark-up of texts. To continuously improve the corpus, we would be grateful, if you could bring any errors you may discover to our attention by [creating an issue](https://github.com/mappingtreaties/tota/issues).

# License

This project is distributed under the Creative Commons Attribution-NonCommercial 4.0 International license.
