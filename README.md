
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

  - Acquiring WeStCOMS outputs from the Scottish Association of Marine
    Sciences (SAMS) thredds server;
  - Processing WeStCOMS outputs;
  - Computing new new fields;
  - Building the WeStCOMS unstructured mesh(es) as spatial objects and
    locating cells and coordinates;
  - Extracting and interpolating model predictions;
  - Exploring environmental conditions through space and time with
    statistical summaries and maps;
  - Validating WeStCOMS predictions with observations, including from
    diverse animal movement datasets;

## Installation

You can install the released version of WeStCOMSExploreR from
[CRAN](https://CRAN.R-project.org) with:

``` r
#### install from CRAN
install.packages("WeStCOMSExploreR")
```

``` r
#### Or, install the development version from github
devtools::install_github("edwardlavender/WeStCOMSExploreR")
```

## Acquire files

  - `thredds_url()` - list URLs from which to extract or download model
    outputs on the SAMS thredds server;
  - `thredds_extract()` - extract model outputs from the SAMS thredds
    server;
  - `thredds_download()` - download files from the SAMS thredds server;

## Process files

Hydrodynamic model outputs are typically stored as MATLAB® or Network
Common Data Form (NetCDF) files. To use these in `R`, some
pre-processing outside of `R` may be required. This is described in the
vignette. Some functions are designed to facilitate processing WeStCOMS
outputs. These include:

  - `date_name()` - flick between dates and WeStCOMS file names;
  - `create_wcdirs()` - create folders in which to store WeStCOMS
    outputs;
  - `define_dates2load()` - define a sequence of dates for which to load
    WeStCOMS files, accounting for corrupt files;
  - `WeStCOMSarray2df()` - convert a WeStCOMS array to a dataframe for
    plotting (see later);

## Build unstructured mesh(es)

Several functions are designed to facilitate building and working with
unstructured meshes. These include:

  - `build_mesh()` - build an unstructured mesh (around nodes or
    elements) from node coordinates and connections as a
    `SpatialPolygonsDataFrame` in R;
  - `find_cells()` - find the mesh cells (for nodes or elements) which
    enclose inputted coordinates;
  - `find_xy()` - find the coordinates of mesh cells (for nodes or
    elements);

## Compute new fields

Some functions are designed to compute new 2-dimensional fields, either
using existing hydrodynamic model outputs (such as current speed) or
from scratch (such as sun angle) in cases where it is helpful to express
variables which are not resolved by the hydrodynamic model across the
same mesh (for instance, to investigate the extent of spatiotemporal
variation over the same spatial domain). These include the following:

  - `compute_field_current_direction()` - compute current direction from
    \(u\) and \(v\) component vectors;
  - `compute_field_current_speed()` - compute current speed from \(u\)
    and \(v\) component vectors;
  - `compute_field_wind_direction()` - compute wind direction from \(u\)
    and \(v\) component vectors;
  - `compute_field_wind_speed()` - compute wind speed from \(u\) and
    \(v\) component vectors;
  - `compute_field_thermocline()` - compute thermoline strength as a new
    field;
  - `compute_field_sun_angle()` - compute sun angle as a new field;
  - `compute_field_photoperiod()` - compute photoperiod as a new field;
  - `compute_field_depth()` - compute the depths of Sigma layers,
    extracting parameters from model outputs as necessary;
  - `compute_field()` - compute multiple new 2 dimensional hydrodynamic
    fields (namely, thermocline strength, wind speed, wind direction,
    current speed, current direction and sun angle) from model outputs
    at the same time;

## Extract model predictions

Some functions are designed to faciliate the extraction of model
predictions from source files. These include the following:

  - `exclude_corrupt()` and `exclude_unavailable()` exclude corrupt and
    unavailable files from file names vectors;
  - `extract()` - extract WeStCOMS predictions for multiple
    dates/hours/layers/mesh cells;
  - `depth_layer_calc()` - calculate the depth of Sigma layers;
  - `depth_layer_add()` - add the depths of Sigma layers to a dataframe;
  - `depth_layer_assign()` - assign the Sigma layers to a dataframe
    based on the depth;
  - `interp_layer()`, `interp_btw_hours()` and `interp_btw_depths()` -
    interpolate fractional layer numbers and predictions between hours
    or layers;

## Explore environmental conditions

Some functions are designed to facilitate exploration of environmental
conditions through space and/or time. These include the following:

  - `summarise2dfield()` - compute statistical summaries of
    environmental conditions across a WeStCOMS layer (through time for a
    given WeStCOMS file, if applicable);
  - `plot2dfield()` - visualise environmental conditions across a
    WeStCOMS layer through space at a specified point in time;
  - `explore()` - implement `summarise2dfield()` and `plot2dfield()`
    across multiple timepoints and/or WeStCOMS files;
  - Additional plotting functions are available in the `prettyGraphics`
    package, including `pretty_scape_3d()` and `vis_scape_3d()` which
    produce interactive, 3-dimensional visualisations of
    landscapes/seascapes and/or environmental conditions; for large
    rasters, `crop_aggr_utm()` helps reduce raster dimensions for these
    functions;

## Validate model predictions

`validate()` facilitates the comparison of observed conditions
(including those from animal movement datasets) with predicted
conditions to evaluate WeStCOMS skill.

## Future functionality

Future plans for `WeStCOMSExploreR` include developing the following
functionality:

  - Exploring temperature profiles through space and time;
  - Exploring spatiotemporal variation in environmental conditions in
    3d;
  - Estimating bottom velocity from vertical profiles;
  - Improved flexibility to define new environmental fields;
