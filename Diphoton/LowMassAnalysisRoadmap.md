# Low Mass Analysis Roadmap
The purpose of this document is to lay out a roadmap for how the low mass Analysis
should be done. This will serve as a way to completely understand what was done
in the past and what will be needed in the future.


## Diphoton Selection
The diphoton selection is as follows:

  - At least two photons passing tight ID
  - Both photons must be in $|\eta| < 2.37$ excluding crack
  - $E_t > 22 GeV$
  - Both photons must pass Isolation
    - Tracker Iso - Scalar sum of all tracks with Pt > 1GeV in a cone of 0.2
    around each photon must be less than 2.6 GeV.
    - Calo Iso - Transverse energy sum of clusters with positive energy in radius
    of 0.4 must be less than 6 GeV.
  - Photon pointing method is used to find vertex.

We will be using the **HLT_2g20_tight_icalovloose_L12EM15VHI** and **HLT_2g20_tight_icalotight_L12EM15VHI** triggers for this analysis. This allows
us to use a 22 GeV Et cut and puts the kinematic turn on between 40 and 60 GeV
away from the Z peak.

## Data Sample and Trigger
Must measure efficiency of trigger.

## MC Samples
For masses below 150 GeV the SM higgs width was used. Above 150 GeV a width of
4.07 MeV is used (Narrow Width Approximation).

Study the signal shape with other production modes to make sure limits are model
independent. In the past the modes used were VBF, WH/ZH and ttH.


Determine the fit function for the signal. Use double sided crystal ball function.
To do this we fit the DSCB separately for each mass point used. Then the evolution
of each of the parameters is fit to get parameterizations of each. This gives us the functional form and a fit to each of the single mass points. They then used
these parameterizations for a binned multiple mass point fit where all masses are
fit at the same time. So evey mass is plotted then the parameterization functions
are plugged into the DSCB for each of its paramters and the fit is redone. This
is then used for the actual signal paramterization when scanning over the data.
For low mass this should be repeated for each of the three conversion categories.

## Background Modeling

In the paper they cary out a test on whether catagorization in converted vs.
unconverted photons is necessary, but I do not think that we need to do this
again. I think that catagorizing is necessary.

### Electron Backgrounds
Electron backgrounds come from misidentification of electrons from the
Drell-Yan process. This background is estimated from a dielectron sample using
the photon reconstruction algorithms with no isolation applied. Because the
photons come from electron bremsstrahlung their kinematics are slightly
different than from electons and the shape must be corrected.

### Electron to Photon Fake Rates
Use dielectron and electron-photon events in a window around the Z peak in
data. A template of the Drell-Yan background is then made.

### Non-resonant Background Modeling
Spurious signal method. Need to investigate new methods (SWiFt).

### SM Higgs Background
Since we are only searching up to 100 GeV, we shouldnt have to worry about this.

## Systematic Uncertainties.
Lots of systematics to evaluate.

  * Production Mode
  * Pile-up
  * Energy Resolution
  * Conversion Catagory
  * Photon ID
  * Photon Isolation
  * Template fit (Z->ee)

## Results
Statistics and cross section limits.
