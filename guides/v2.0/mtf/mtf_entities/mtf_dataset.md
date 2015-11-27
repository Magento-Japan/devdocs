---
layout: default
group: mtf-guide
subgroup: D_Entities
title: Entities of the Magento Testing Framework
menu_title: Data set
menu_order: 8
github_link: mtf/mtf_entities/mtf_dataset.md
---

<h2>Data set</h2>

* TOC
{:toc}

##Data set overview
Data sets contain data used by test case and constraints.
A data set can have several variations.
Each variation has constraints that are called at the end of the test flow.

##Data set structure

Data set is an XML file that contains test variations for a test case.

Variation includes:

- Data used during the test flow and assertions
- [Constraints][] that will be called after test flow

The following table shows structure of the data set:

<table>
<col width="1*">
<col width="1*">
<col width="2*">
<tr><th>Node </th><th>Semantics </th><th>Attributes </th></tr>
<tr>
<td><code>config</code> </td>
<td>The root element that defines an XML namespace and an XML Schema. </td>
<td><ul>
<li><code> xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"</code></li>
<li><code>xsi:noNamespaceSchemaLocation="../../../../../../vendor/magento/mtf/etc/variations.xsd"</code></li>
</ul> </td>
</tr>
<tr>
<td><code>testCase</code> </td>
<td>Contains a reference to the test case class in attribute and variations in child elements. </td>
<td><ul>
<li><code>name</code> - full name of a test case class. Required.</li>
<li><code>summary</code> - description of a test case. Required.</li>
<li><code>ticketId</code> - identifier of related ticket. Optional.</li>
</ul> </td>
</tr>
<tr>
<td><code>variation</code></td>
<td>Contains variation description in attributes and data with constraints in child elements.</td>
<td><ul>
<li><code>name</code> - a variation name. Required.</li>
<li><code>firstConstraint</code> - a full name of constraint that is performed first. Optional.</li>
<li><code>method</code> - a name of the test method from the test class. Optional.</li>
<li><code>summary</code> - description of the variation. Optional.</li>
<li><code>ticketId</code> - an identifier of the related ticket. Optional.</li>
</ul></td>
</tr>
<tr>
<td><code>data</code> </td>
<td>Data to be used by a test case. </td>
<td><ul>
<li><code>name</code> - a name of variable with extra data. A format can be the following: <i>entity_name</i>/<code>data</code>/<i>name_of_the_field</i>, for example <code>product/data/name</code>. The processing logic is defined in <a href="https://github.com/magento/mtf/blob/develop/Magento/Mtf/Fixture/InjectableFixture.php">InjectableFixture</a> class. Required.</li>
<li><code>xsi:type</code> - a type of the value. 
The following data types are available:
<ul>
<li><code>array</code></li>
<li><code>string</code></li>
<li><code>boolean</code></li>
<li><code>object</code></li>
<li><code>number</code></li>
<li><code>null</code></li>
</ul></li>Required.
</ul> </td>
</tr>
<tr>
<td><code>constraint</code></td>
<td>Reference to the constraint class performed after the test flow.  </td>
<td><ul>
<li><code>name</code> - a full name of the constraint class. Required.</li>
<li><code>next</code> - a full name of the constraint class performing next in a queue. Optional.</li>
<li><code>prev</code> - a full name of the constraint class performing previous in a queue. Optional.</li>
</ul></td></tr>
</table>

<div class="bs-callout bs-callout-warning">
  <p>Variation should contain only data that is required for its flow and constraints.</p>
</div>

<div class="bs-callout bs-callout-tip">
  <p>Data with name <code>tag</code> can be used to customize test suite run.</p>
</div>

Let's see an example:

{%highlight xml%}
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="../../../../../../../vendor/magento/mtf/etc/variations.xsd">
    <testCase name="Magento\Catalog\Test\TestCase\Product\CreateSimpleProductEntityTest" summary="Create Simple Product" ticketId="MAGETWO-23414">
        <variation name="CreateSimpleProductEntityTestVariation1" summary="Create product with custom options(fixed price)">
            <data name="product/data/url_key" xsi:type="string">simple-product-%isolation%</data>
            <data name="product/data/name" xsi:type="string">Simple Product %isolation%</data>
            <data name="product/data/sku" xsi:type="string">simple_sku_%isolation%</data>
            <data name="product/data/price/value" xsi:type="string">10000</data>
            <data name="product/data/short_description" xsi:type="string">Simple Product short_description %isolation%</data>
            <data name="product/data/description" xsi:type="string">Simple Product description %isolation%</data>
            <data name="product/data/weight" xsi:type="string">50</data>
            <data name="product/data/quantity_and_stock_status/qty" xsi:type="string">657</data>
            <data name="product/data/custom_options/dataset" xsi:type="string">drop_down_with_one_option_fixed_price</data>
            <data name="product/data/checkout_data/dataset" xsi:type="string">simple_drop_down_with_one_option_fixed_price</data>
            <data name="product/data/price/dataset" xsi:type="string">drop_down_with_one_option_fixed_price</data>
            <constraint name="Magento\Catalog\Test\Constraint\AssertProductSaveMessage" />
            <constraint name="Magento\Catalog\Test\Constraint\AssertProductInGrid" />
            <constraint name="Magento\Catalog\Test\Constraint\AssertProductInCategory" />
            <constraint name="Magento\Catalog\Test\Constraint\AssertProductPage" />
            <constraint name="Magento\Catalog\Test\Constraint\AssertProductInCart" />
        </variation>
    </testCase>
</config>
{%endhighlight xml%}

This is a data set that:

- corresponds to the XSD schema `<magento2>/dev/tests/functional/vendor/magento/mtf/etc/variations.xsd`
- relates to the `Magento\Catalog\Test\TestCase\Product\CreateSimpleProductEntityTest` test (performs creation of the simple product) 
- relates to the ticket `MAGETWO-23414` in Jira
- contains variation `CreateSimpleProductEntityTestVariation1` that creates product with fixed price with the following data (corresponds to the `Magento\Catalog\Test\Fixture\CatalogProductSimple` fixture):
  - `url_key` field is assigned with `simple-product-%isolation%`. [More info about %isolation% usage]({{site.gdeurl}}mtf/mtf_entities/mtf_fixture-repo.html#mtf_repo_isolation).
  - `name` field is assigned with `Simple Product %isolation%`
  - `sku` field is assigned with `simple_sku_%isolation%`
  - `price` field is processed by a [data source][] `Magento\Catalog\Test\Fixture\Product\Price` and is assigned `10000`
  - `short_description` field is assigned with `Simple Product short_description %isolation%`
  - `description` field is assigned with `Simple Product description %isolation%`
  - `weight` field is assigned with `50`
  - `quantity_and_stock_status/qty` field is assigned with `657`
  - `custom_options` field is processed by a [data source][] `Magento\Catalog\Test\Fixture\Product\CustomOptions` using a data set `drop_down_with_one_option_fixed_price` from the repository `Magento\Catalog\Test\Repository\Product\CustomOptions`
  - `checkout_data` fields are assigned with a data set `simple_drop_down_with_one_option_fixed_price` from the `Magento\Catalog\Test\Repository\CatalogProductSimple\CheckoutData` repository
  - `price` fields are assigned with a data set `drop_down_with_one_option_fixed_price` from the `Magento\Catalog\Test\Repository\CatalogProductSimple\Price` repository. This data set is used by [constraint][].

You'll have the following structure:

<p><a href="{{ site.baseurl }}common/images/Data set2.png"><img src="{{ site.baseurl }}common/images/Data set2.png"/></a></p> 

[Constraints]: {{site.gdeurl}}mtf/mtf_entities/mtf_constraint.html
[constraint]: {{site.gdeurl}}mtf/mtf_entities/mtf_constraint.html
[fixtures]: {{site.gdeurl}}mtf/mtf_entities/mtf_fixture.html
[data source]: {{site.gdeurl}}mtf/mtf_entities/mtf_fixture.html#mtf_fixture_source

*[MTF]: Magento Testing Framework
