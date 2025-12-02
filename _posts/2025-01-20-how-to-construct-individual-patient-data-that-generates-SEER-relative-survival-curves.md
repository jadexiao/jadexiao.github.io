---
layout: post
title: how to construct individual patient data that generates SEER relative survival curves
date: 2025-01-20
tags: [simulation, code]
permalink: /blog/how-to-construct-individual-patient-data-that-generates-SEER-relative-survival-curves/
type: blog
---

<div class="blog-text">
    <p>The National Cancer Institute's (NCI's) Surveillance, Epidemiology, and End Results (SEER) cancer statistics database provides three different types of summary survival curves:</p>

    <ul>
        <li><b>Observed survival:</b> The proportion of patients who have not died of any cause by time \(t\) since diagnosis.</li>
        <li><b>Expected survival:</b> The *expected* proportion of patients who have not died of any cause by time \(t\) since diagnosis, based on the all-cause mortality of a comparable group of people with respect to age, sex, race, calendar year, etc.</li>
        <li><b>Relative survival:</b> The proportion of patients who have not died of cancer by time \(t\) since diagnosis, computed as the ratio of observed to expected survival.</li>
    </ul>

    <p> Survival curve fitting requires individual patient data (IPD) as an input. IPD can be constructed from counts of patients, deaths, and censored cases, which the SEER database provides in the following format:</p>

    <ul>
        <li>\(N(t)\): The number of patients still under observation by time \(t\) since diagnosis.</li>
        <li>\(D(t)\): The number of any-cause deaths by time \(t\) since diagnosis.</li>
        <li>\(C(t)\): The number of patients lost to follow-up by time \(t\) since diagnosis.</li>
    </ul>

    <p>Constructing IPD for observed survival is straightforward since \(N(t)\), \(D(t)\), \(C(t)\) can be used directly. Constructing IPD for relative survival is not straightforward because \(N(t)\), \(D(t)\), \(C(t)\) need to be adjusted to reflect cancer deaths only. This tutorial will demonstrate how to do so.</p>

    <p style='color: #B509AC'><strong style='color: #B509AC'>MASSIVE DISCLAIMER!!!</strong> I am in no way claiming that this is the right thing to do. To be totally correct, i.e., abiding by the definition of relative survival, one should generate IPD for observed and expected survival, fit the curves separately, then compute relative survival as their ratio. The below method is simply a hack to quickly generate relative survival curves. It will not preserve the relationship between observed, expected, and relative survival after curve fitting. Proceed with caution.</p>

    <p>Let \(R(t)\) denote the *interval* (NOT cumulative) relative survival probabilities. This tells us the proportion of patients from time \(t-1\) who are still alive at time \(t\) for \(t>0\), with \(R(0)=1\).</p>

    <p>The number of patients under observation does not change, so:</p>

    <p class="text-center">\(N^\ast(t)=N(t).\)</p>

    <p>The number of censored cases should be augmented with the number of non-cancer deaths, since their death from other causes effectively renders their time of cancer death unobservable:</p>

    <p class="text-center">\(C^\ast(t)=C(t)+D(t)-D^\ast(t).\)</p>

    <p>Now since we are reframing cancer survival as observed survival, we have the following relationship (using the actuarial method):</p>

    <p class="text-center">\(\displaystyle R(t)=1-\frac{D^\ast(t)}{N^\ast(t)-\tfrac{1}{2}C^\ast(t)}.\)</p>

    <p>Solving for \(D^\ast(t)\) yields:</p>

    <p class="text-center">\(\displaystyle D^\ast(t)=\frac{\big(2N(t)-C(t)-D(t)\big)\big(1-R(t)\big)}{1+R(t)}.\)</p>

    <p>The remaining step is to construct the IPD itself. The precise methodology is detailed elsewhere, e.g., <a href="https://doi.org/10.1186/1471-2288-11-139" target="_blank">Hoyle et al. (2011)</a>.</p>

    <p>Below is a sample calculation using SEER data for stage I breast cancer diagnosed at age 50 years:</p>

    <div class="blog-img">
        <img style="--large-width: 100%" src="{{ site.baseurl }}/assets/img/blog/2025-01-20-how-to-construct-individual-patient-data-that-generates-SEER-relative-survival-curves-1.png">
    </div>

    <div>
        <img style="width: 81.85%" src="{{ site.baseurl }}/assets/img/blog/2025-01-20-how-to-construct-individual-patient-data-that-generates-SEER-relative-survival-curves-2.png">
    </div>
</div>
