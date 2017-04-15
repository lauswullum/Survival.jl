# Kaplan-Meier estimator

The [Kaplan-Meier estimator](https://en.wikipedia.org/wiki/Kaplan-Meier_estimator)
is a nonparametric estimator of the survivor function, i.e. the probability of survival
beyond a given time.

The estimate is given by

``
\hat{S}(t) = \prod_{i: t_i < t} \left( 1 - \frac{d_i}{n_i} \right)
``

where ``d_i`` is the number of observed events at time ``t_i`` and ``n_i`` is the
number of subjects at risk for the event just before time ``t_i``.

The pointwise standard error of the log of the survivor function can be computed
using Greenwood's formula:

``
\text{SE}(\log \hat{S}(t)) = \sqrt{\sum_{i: t_i < t} \frac{d_i}{n_i (n_i - d_i)}}
``

## API

```@meta
CurrentModule = Survival
```

```@docs
Survival.KaplanMeier
StatsBase.fit(::Type{Survival.KaplanMeier}, ::Any, ::Any)
StatsBase.confint(::Survival.KaplanMeier, ::Any)
```

## References

* Kaplan, E. L., and Meier, P. (1958). *Nonparametric Estimation from Incomplete
  Observations*. Journal of the American Statistical Association, 53(282), 457-481.
  doi:10.2307/2281868

* Greenwood, M. (1926). *A Report on the Natural Duration of Cancer*. Reports on
  Public Health and Medical Subjects. London: Her Majesty's Stationery Office.
  33, 1-26.