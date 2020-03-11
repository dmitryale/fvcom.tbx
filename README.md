
<!-- README.md is generated from README.Rmd. Please edit that file -->

# WeStCOMSExploreR

<!-- badges: start -->

<!-- badges: end -->

`WeStCOMSExploreR` is an R package which provides tools for the
exploration of unstructured, prism-based hydrodynamic model outputs
(i.e. from the Finite Coastal Ocean Volume Model, FVCOM) in `R`. The
package has been designed specifically for the West Coast of Scotland
Coastal Modelling System (WeStCOMS), which implements FVCOM. Package
development has been motivated by the requirements of ecological
research, and the need to link hydrodynamic model outputs with
ecological analyses implemented in `R`. To this end, the package
includes functions which facilitate the following operations:

  - Processing WeStCOMS outputs, including the definition of new fields;
  - Building the WeStCOMS unstructured mesh(es) as spatial objects;
  - Exploring environmental conditions through space and time, with
    statistical summaries and maps;

## Installation

You can install the released version of WeStCOMSExploreR from
[CRAN](https://CRAN.R-project.org) with:

``` r
#### install from CRAN
install.packages("WeStCOMSExploreR")
```

``` r
#### Or, install the development version from github
# ... 
```

## Prerequisites

WeStCOMS files are MATLAB® files. To use these in R, some pre-processing
outside of R is required (see the vignette).

## Processing WeStCOMS outputs

Some functions are designed to facilitate processing WeStCOMS outputs.
This includes the following:

  - `date.name()` - flick between dates and WeStCOMS file names;
  - `define.dir()` - create folders in which to store WeStCOMS outputs;
  - `define.dates2load()` - define a sequence of dates for which to load
    WeStCOMS files, accounting for corrupt files;
  - `define.new2dfield()` - define new 2 dimensional hydrodynamic fields
    from WeStCOMS outputs (namely, themormocline stength, wind speed,
    wind direction, current speed, current direction and sun angle);
  - `sun.angle.across.mesh()` - compute sun angle as a WeStCOMS field;
  - `WeStCOMSarray2df()` - convert a WeStCOMS array to a dataframe for
    plotting (see later);

## Unstructured mesh(es)

`build.mesh()` builds an unstructured mesh (around nodes or elements)
from node coordinates and connections as a SpatialPolygonsDataFrame in
R.

## Explore environmental conditions

Some functions are designed to facilitate exploration of environmental
conditions through space and/or time. These include the following:

  - `summarise2dfield()` - compute statistical summaries of
    environmental conditions across a WeStCOMS layer (through time for a
    given WeStCOMS file if applicable);
  - `plot2dfield()` - visualise environmental conditions across a
    WeStCOMS layer through space at a specified point in time;
  - `explore.WeStCOMS()` - implement `summarise2dfield()` and
    `explore.WeStCOMS()` across multiple timepoints and/or WeStCOMS
    files;

## Future functionality

Future plans for `WeStCOMSExploreR` include developing the following
functionality:

  - Creating interactive bathymetry plots;
  - Exploring temperature profiles through space and time;
  - Exploring spatiotemporal variation in environmental conditions in
    3d;
  - Defining bottom velocity from vertical profiles;
  - Flexibility to define new environmental fields more easily;
