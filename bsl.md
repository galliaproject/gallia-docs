# FAQ for Gallia's Business Source License (BSL)

__Disclaimer__: _this page provides information on how to interpret Gallia's BSL license in <ins>non-legal terms</ins>, it therefore does not supersede the terms of [the actual license](https://github.com/galliaproject/gallia-core/blob/master/LICENSE) in any way._

### 1. What is the "Business Source License" (BSL)?

Per MariaDb's [own BSL FAQ](https://mariadb.com/bsl-faq-adopting/#whatis) on the matter (they created BSL):

> _[BSL](https://mariadb.com/bsl11/) is an alternative to closed source or open core licensing models. Under BSL, the source code is always publicly available. Non-production use of the code is always free, and the licensor can also make an Additional Use Grant allowing limited production use. Source code is guaranteed to become Open Source at a certain point in time. On the Change Date, or the fourth anniversary of the first publicly available distribution of the code under the BSL, whichever comes first, the code automatically becomes available under the Change License. The Change License is mandated to be GPL Version 2.0 or later or a compatible license (i.e., the Change License is always an Open Source license that enables use of the software in a GPL project)."_

### 2. What is the intent captured in Gallia's version of BSL?

The intent of the license terms, especially the [_Additional Use Grant_](https://github.com/galliaproject/gallia-core/blob/master/LICENSE#L9) section, is for Gallia to be free for any __essential__ OR __small-enough__ entity. On the other hand, it is expected that any non-essential organization above a certain threshold in size<sup>[[1]](#size)</sup> __can afford__ to retribute the project in exchange for using it.

If you feel like the current license terms are not actually aligned with the stated intent above - especially for edge cases - please reach the author at <sub><img src="./images/ct.png"></sub> to discuss the specifics.


### 3. Is the BSL an Open Source license?

Per MariaDb's [own BSL FAQ](https://mariadb.com/bsl-faq-adopting/#osl) on the matter (they created BSL):

> _The BSL does not meet the [Open Source Definition](https://en.wikipedia.org/wiki/The_Open_Source_Definition) (OSD) maintained by the [Open Source Initiative](https://en.wikipedia.org/wiki/Open_Source_Initiative) (OSI). OSD does not allow limitations on specific kinds of such, such as production use. However, most of the OSD criteria are met. Most important, the source code is made available. The BSL allows for copying, modification, creation of derivative works, redistribution, and non-production use of the code. It allows for (and encourages) the licensor to define an Additional Use Grant (e.g., allowing for free use below a specified level, like in [this example](https://github.com/mariadb-corporation/MaxScale/blob/2.5/LICENSE25.TXT))._

### 4. Why not an open source license right away?

It is the understanding of the author that many open source projects struggle to secure sufficient funding, especially when they're not backed by an existing organization. They can also be outright exploited: think white-labeling, or open source tools wrapped almost as-is around a subscription-based "service".

The author will expand on that choice in a separate article, but in the meantime, the footnotes<sup>[[2]](#inspiration)</sup> list some articles that motivated this decision.

### 5. Why four years for the _"Change Date"_ (to Apache 2)?

The author currently works alone on the project and therefore needs enough of a buffer to get established and expand. The number of years in the _Change Date_ is likely to go down as the project gets funded and the team grows. Apache 2 is likely to remain the target license no matter what.

### 6. Who else uses BSL?

This article by _Adam Retter_ does a nice job summarizing adoption as of March 2020: ["Business Source License Adoption"](https://blog.adamretter.org.uk/business-source-license-adoption/)

### 7. Can I still contribute code and how?

Yes, WIP (see [MariaDB](https://mariadb.com/bsl-faq-adopting/#contrib))

<hr/>

- <a name="size"></a><sup>[1]</sup> Currently using &lt;200 employees and &lt;$2M in revenue as proxy for "small"
- <a name="inspiration"></a><sup>[2]</sup> In no particular order:
  - ["Open source has a funding problem"](https://stackoverflow.blog/2021/01/07/open-source-has-a-funding-problem/) by James Turner (_Jan 2021_)
  - ["Open Source Business Models Considered Harmful"](https://medium.com/@johnmark/open-source-business-models-considered-harmful-2e697256b1e3) by John Mark (_Jan 2019_)
  - ["MariaDB Fixes it's Business Source License With My Help, Releases MaxScale 2.1 Database Routing Proxy"](https://perens.com/2017/02/14/bsl-1-1/) by Bruce Perens (_Feb 2017_)
  - ["Why Funding Open Source is Hard"](https://hackernoon.com/why-funding-open-source-is-hard-652b7055569d) by Eric Berry (_Dec 2017_)
  - ["Not all open source is created equal"](https://www.computerweekly.com/blog/Data-Matters/Not-all-open-source-is-created-equal) by Marc Linster (_Jun 2020_)
  - ["Business Source License Adoption"](https://blog.adamretter.org.uk/business-source-license-adoption/) by Adam Retter (_Mar 2020_)
  - ["Lack of leadership in open source results in source-available licenses"](https://techcrunch.com/2019/05/30/lack-of-leadership-in-open-source-results-in-source-available-licenses) by Salil Deshpande (_May 2019_) 
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>

