---
layout: post
title: resources for simulation modeling and cost-effectiveness analysis
date: 2025-02-03
description:
tags: cea simulation
categories:
---
<i>Last updated: February 3, 2025</i>

These are some good resources for standard inputs to (US-based) simulation modeling and cost-effectiveness analysis.

<p style="margin-top: 25px"></p>

**Demographics**
* <a href="https://www.census.gov/topics/population/age-and-sex/data/tables.html" target="_blank">United States Census Bureau - Age and Sex Tables</a>
* <a href="https://wonder.cdc.gov/single-race-population.html" target="_blank">CDC WONDER Single-Race Population Estimates

<p style="margin-top: 25px"></p>

**Mortality**
* <a href="https://www.lifetable.de" target="_blank">Human Life-Table Database</a>: Collated life tables for 142 regions over many years with stratification by age, sex, race, etc.
* <a href="https://wonder.cdc.gov/ucd-icd10-expanded.html" target="_blank">CDC WONDER Underlying Cause of Death</a>: Mortality rates stratified by cause of death, year, region, age, sex, race, etc.

<p style="margin-top: 25px"></p>

**Population health**
* <a href="https://www.cdc.gov/nchs/nhanes/about/index.html" target="_blank">National Health and Nutrition Examination Survey (NHANES)</a>: A national survey on general health and nutrition, with data collected from interviews, health exams, and laboratory tests conducted on ~5,000 adults and children each year.
* <a href="https://www.cdc.gov/nchs/nhis/index.html" target="_blank">National Health Interview Survey (NHIS)</a>: A national survey on a broad range of health-related topics, with data collected through confidential face-to-face interviews of ~27,000 adults each year. Specifically the <a href="https://archive.cdc.gov/www_cdc_gov/nchs/nhis/nhis_2015_data_release.htm" target="_blank">2015 Data Release</a> which included a cancer-focused questionnaire.
* <a href="https://www.cdc.gov/brfss/index.html" target="_blank">Behavioral Risk Factor Surveillance System (BRFSS)</a>: A national survey on health-related risk behaviors, chronic health conditions, and use of preventive services, with data collected through telephone interviews of >400,000 adults each year.

<p style="margin-top: 25px"></p>

**Healthcare costs**
* <a href="https://www.mdsave.com" target="_blank">MDSave</a>: Cost of medical procedures by ZIP code.

<p style="margin-top: 25px"></p>

**Temporal cost conversion**
* <a href="https://fred.stlouisfed.org/data/CPIMEDSL" target="_blank">Consumer Price Index (CPI)</a>: The CPI ratio between a previous year and the current year can be used to convert historical prices to current day prices.

<p style="margin-top: 25px"></p>

**Age-related quality-of-life weights**
* Hanmer J et al. Report of nationally representative values for the noninstitutionalized US adult population for 7 health-related quality-of-life scores. <i>Med Decis Making</i> 2006;26(4):391-400. <a href="https://doi.org/10.1177/0272989X06290497" target="_blank">https://doi.org/10.1177/0272989X06290497</a>

<p style="margin-top: 25px"></p>

**Cancer**
* <a href="https://wonder.cdc.gov/cancer.html" target="_blank">CDC WONDER Cancer Statistics</a>: Incidence and mortality rates stratified by cancer site, year, region, age, sex, race, etc.
* <a href="https://gis.cdc.gov/Cancer/USCS/#/AtAGlance/" target="_blank">Cancer Statistics</a>: Incidence and mortality rates, survival, prevalence, screening adherence, risk factors.

<p style="margin-top: 25px"></p>

**Continous-time agent-based modeling using ConcurrentSim (formerly SimJulia)**
* <a href="SimJulia Documentation" target="_blank">SimJulia Documentation</a>: Webpage format.
* <a href="https://simjuliajl.readthedocs.io/_/downloads/en/stable/pdf/" target="_blank">SimJulia Documentation</a>: PDF format.
* <a href="https://juliadynamics.github.io/ConcurrentSim.jl/stable/" target="_blank">ConcurrentSim Documentation</a>: Webpage format; newer but less comprehensive than the SimJulia documentation.
* <a href="https://github.com/JuliaDynamics/ConcurrentSim.jl" target="_blank">ConcurrentSim.jl</a>: GitHub respository.
* <a href="https://www.juliahealthcare.org/simjulia_index.html" target="_blank">Julia for healthcare modelling and data science</a>: Extremely helpful example code for hospital bed and emergency department simulation.
