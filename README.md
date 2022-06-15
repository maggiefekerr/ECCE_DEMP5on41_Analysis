# Maggie Kerr (mkerr@mta.ca)
# Mount Allison University
# ECCE_DEMP5on41_Analysis

Analysis module for 5 on 41 GeV DEMP events after having pass through the Fun4All simulation. Research is for the future EIC (Diffractive and Tagging working group).

Drawn from Stephen Kay's analysis module : https://github.com/sjdkay/ECCE_DEMP_Analysis.

Installation

1) To install virtual machine (VM), follow directions from the following link : https://github.com/ECCE-EIC/Singularity/blob/master/VirtualBox.md.

2) THe following steps will install general EIC macros onto the VM:
Within VM:
Open new terminal
~/singularity_shell.sh
source setup.sh
mkdir work
cd work
git clone https://github.com/ECCE-EIC/macros
git clone https://github.com/ECCE-EIC/tutorials

3) Specifically for cloning this repository:
Within work directory of VM:
git clone https://github.com/maggiefekerr/ECCE_DEMP5on41_Analysis
mkdir ECCE_DEMP5on41
cd ECCE_DEMP5on41
CreateSubsysRecoModule.pl ECCE_DEMP5on41
cp ~/work/tutorials/CaloAna/src/*.[sa]* .
cp ~/work/ECCE_DEMP_Analysis/ECCE_DEMP_Ana/configure.ac ./
cp ~/work/ECCE_DEMP_Analysis/ECCE_DEMP_Ana/Makefile.am ./
chmod +x autogen.sh
mkdir build
cd build
../autogen.sh --prefix=$MYINSTALL
make install

4) Copying in the latest version of the respository and then rebuilding your directory
Within ~/workECCE_DEMP5on41/build directory:
cp /home/fun4all/work/ECCE_DEMP_Analysis/ECCE_DEMP5on41_Ana/ECCE_DEMP5on41.* ../
make install

5) Whenever you are rebuilding your plugin (it is recommended to make changes to G4_User.C and Fun4all_reana.C within your ECCE_DEMP5on41_Analysis repository):
cd /home/fun4all/work/macros/detectors/EICDetector
cp ~/work/ECCE_DEMP5on41_Analysis/main_macro/G4_User.C .
cp ~/work/ECCE_DEMP5on41_Analysis/main_macro/Fun4all_reana.C .
