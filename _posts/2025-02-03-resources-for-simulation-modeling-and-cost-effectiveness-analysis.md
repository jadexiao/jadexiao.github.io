---
layout: post
title: resources for simulation modeling and cost-effectiveness analysis
date: 2025-02-03
tags: [cea, simulation, data]
permalink: /blog/resources-for-simulation-modeling-and-cost-effectiveness-analysis/
type: blog
---

<div class="blog-text">
    <p><i>Last updated: November 29, 2025</i></p>

    <p>These are some good resources for standard inputs to (US-based) simulation modeling and cost-effectiveness analysis.</p>

    <p class="blog-list-heading">Demographics</p>

    <ul>
        <li><a href="https://www.census.gov/topics/population/age-and-sex/data/tables.html" target="_blank">[ U.S. Census Bureau ] Age and Sex Tables</a>: Select the "All" tab to find the latest "Age and Sex Composition in the United States (YEAR)" file.</li>
        <li><a href="https://wonder.cdc.gov/single-race-population.html" target="_blank">[ CDC WONDER ] Single-Race Population Estimates</a>: Stratification by year, region, sex, race, and age.</li>
    </ul>

    <p class="blog-list-heading">Mortality rates</p>

    <ul>
        <li><a href="https://www.lifetable.de" target="_blank">Human Life-Table Database</a>: Collated life tables for 142 regions over many years with stratification by age, sex, race, etc.</li>
        <li><a href="https://wonder.cdc.gov/deaths-by-underlying-cause.html" target="_blank">[ CDC WONDER ] Underlying Cause of Death</a>: Stratification by cause of death, place of death, year, region, sex, race, age, and more.</li>
    </ul>

    <p class="blog-list-heading">Survival analysis</p>

    <ul>
        <li><a href="https://sheffield.ac.uk/nice-dsu/tsds/survival-analysis" target="_blank">[ NICE ] Survival analysis TSD</a>: Best practices for survival analysis.</li>
    </ul>

    <p class="blog-list-heading">Population health</p>

    <ul>
        <li><a href="https://www.cdc.gov/nchs/nhanes/about/index.html" target="_blank">[ CDC ] National Health and Nutrition Examination Survey (NHANES)</a>: National survey on general health and nutrition, with data collected from interviews, health exams, and laboratory tests conducted on ~5,000 adults and children each year.</li>
        <li><a href="https://www.cdc.gov/nchs/nhis/index.html" target="_blank">[ CDC ] National Health Interview Survey (NHIS)</a>: National survey on a broad range of health-related topics, with data collected through confidential face-to-face interviews of ~27,000 adults each year. The <a href="https://archive.cdc.gov/www_cdc_gov/nchs/nhis/nhis_2015_data_release.htm" target="_blank">2015 Data Release</a> is the most recent iteration which includes a cancer-focused questionnaire.</li>
        <li><a href="https://www.cdc.gov/brfss/index.html" target="_blank">[ CDC ] Behavioral Risk Factor Surveillance System (BRFSS)</a>: National survey on health-related risk behaviors, chronic health conditions, and use of preventive services, with data collected through telephone interviews of >400,000 adults each year.</li>
    </ul>

    <p class="blog-list-heading">Healthcare costs</p>

    <ul>
        <li><a href="https://www.medicare.gov/procedure-price-lookup/" target="_blank">[ CMS ] Medicare Procedure Price Lookup Tool</a>: Medicare costs for medical procedures. Make sure to cross-reference with the most recent "(YEAR) Procedure Price Lookup Comparison File" (easiest way to find this file is by Googling the exact name).</li>
        <li><a href="https://www.cms.gov/medicare/payment/fee-schedules/physician/pfs-relative-value-files/" target="_blank">[ CMS ] PFS Relative Value Files</a>: Medicare Physician Fee Schedule. The physician fee for a procedure is the product of the facility/non-facility RVU and the conversion factor.
        </li>
        <li><a href="https://www.mdsave.com" target="_blank">MDSave</a>: Commercial costs for medical procedures.</li>
        <li><a href="https://www.rand.org/health/projects/hospital-pricing.html" target="_blank">[ RAND ] Hospital Price Transparency Study</a>: Medicare-to-commercial cost conversion factors.</li>
    </ul>

    <p class="blog-list-heading">Temporal cost conversion</p>

    <ul>
    <li><a href="https://fred.stlouisfed.org/data/CPIMEDSL" target="_blank">[ U.S. Bureau of Labor Statistics ] Consumer Price Index for All Urban Consumers: Medical Care in U.S. City Average</a>: The CPI ratio between a previous year and the current year can be used to convert historical prices to current day prices.</li>
    </ul>

    <p class="blog-list-heading">Age-related utilities</p>

    <ul>
        <li><a href="https://doi.org/10.1097/MLR.0b013e31814848f1" target="_blank">Fryback et al.</a> US norms for six generic health-related quality-of-life indexes from the National Health Measurement study. <i>Med Care</i> 2007 Dec;45(12):1162-70.</li>
        <li><a href="https://doi.org/10.1177/0272989X06290497" target="_blank">Hanmer et al.</a> Report of nationally representative values for the noninstitutionalized US adult population for 7 health-related quality-of-life scores. <i>Med Decis Making</i> 2006;26(4):391-400.</li>
    </ul>

    <p class="blog-list-heading">Age-related healthcare costs</p>

    <ul>
        <li><a href="https://www.cms.gov/data-research/statistics-trends-and-reports/national-health-expenditure-data/age-and-sex" target="_blank">[ CMS ] National Health Expenditure Data: Age and Sex</a>: Personal healthcare spending by type of good/service, funding source, sex, and age for selected years from 2002 through 2020.</li>
    </ul>

    <p class="blog-list-heading">Cancer statistics</p>

    <ul>
        <li><a href="https://wonder.cdc.gov/cancer.html" target="_blank">[ CDC WONDER ] United States Cancer Statistics</a>: Incidence and mortality rates with stratification by cancer site, year, region, sex, race, and age.</li>
        <li><a href="https://gis.cdc.gov/Cancer/USCS/#/AtAGlance/" target="_blank">[ CDC ] United States Cancer Statistics: Data Visualizations</a>: Visualizations of incidence and mortality rates, survival, prevalence, screening adherence, and risk factors.</li>
    </ul>

    <p class="blog-list-heading">Continous-time agent-based modeling using ConcurrentSim (formerly SimJulia)</p>

    <ul>
        <li><a href="SimJulia Documentation" target="_blank">SimJulia Documentation</a>: Webpage format.</li>
        <li><a href="https://simjuliajl.readthedocs.io/_/downloads/en/stable/pdf/" target="_blank">SimJulia Documentation</a>: PDF format.</li>
        <li><a href="https://juliadynamics.github.io/ConcurrentSim.jl/stable/" target="_blank">ConcurrentSim Documentation</a>: Webpage format; newer but less comprehensive than the SimJulia documentation.</li>
        <li><a href="https://github.com/JuliaDynamics/ConcurrentSim.jl" target="_blank">ConcurrentSim.jl</a>: GitHub respository.</li>
        <li><a href="https://www.juliahealthcare.org/simjulia_index.html" target="_blank">Julia for healthcare modelling and data science</a>: Extremely helpful example code of hospital bed and emergency department simulations.</li>
    </ul>
</div>
