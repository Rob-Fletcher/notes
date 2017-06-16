# MC Production Notes

You first need job options files. The ones I am using are:

    MC15.344000.aMcAtNloPythia8EvtGen_HC_NLO_X0toyy_70_NW.py
    MadGraphControl_HC_NLO_lowmassX0toyy.py

The first file just includes the second. The second file has all the actual
setup in it. The second file also reads the file name of the first and sets
some of the things with that as well. For instance 70GeV particle decaying
with the 'NW' narrow width approximation.

You must setup Athena to run this.

    setupATLAS
    mkdir workarea
    asetup 19.2.5.21,here  # Must set up release that is meant for MC generation
    mkdir run
    cd run  #Put job options in here

You can then run the following command to create the event file.

    Generate_tf.py --ecmEnergy=13000. --maxEvents=100 --runNumber=344000 --firstEvent=1 --randomSeed=123456 --outputEVNTFile=EVNT.root --jobConfig=MC15.344000.aMcAtNloPythia8EvtGen_HC_NLO_X0toyy_70_NW.py

Using that configuration file seems to also do the Pythia8 showering. Next you
need to do the digitization and reconstruction.

There is a script that helps to do the simulation. First I had to setup a newer
version of Athena. I used 20.20.8. Then you can use the command GetTfCommand.py
to show you what command was actually run on some existing file in AMI based on
the tags. So for instance to get the Sim_tf.py command that we need next you can
run:

```bash
setupATLAS
cd workarea
asetup 20.20.8,here
GetTfCommand.py --AMI=s2726  #(put whatever tag you need in here.)
```

This will return something like:

```
PyJobTransforms.<module> 2017-06-13 19:34:49,879 INFO logging set in /cvmfs/atlas.cern.ch/repo/sw/software/x86_64-slc6-gcc49-opt/20.20.8/AtlasCore/20.20.8/InstallArea/share/bin/GetTfCommand.py

Information about tag s2726:
This is a T0 tag.
This tag consists of 1 transform command(s).
Transform commands follow below.
Input and output file names (if present) are only suggestions.

asetup AtlasProduction,19.2.4.9
Sim_tf.py --physicsList 'FTFP_BERT' --truthStrategy 'MC15aPlus' --simulator 'MC12G4' --DBRelease 'default:current' --conditionsTag 'default:OFLCOND-RUN12-SDR-19' --DataRunNumber '222525' --preInclude 'EVNTtoHITS:SimulationJobOptions/preInclude.BeamPipeKill.py,SimulationJobOptions/preInclude.FrozenShowersFCalOnly.py' --geometryVersion 'default:ATLAS-R2-2015-03-01-00_VALIDATION' --postInclude 'default:PyJobTransforms/UseFrontier.py'

Input file arguments:

Output file arguments:

AMI outputs:

```
