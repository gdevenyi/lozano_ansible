# Ansible deployment for lozano lab linux workstations

Ansible deployments scripts designed to be applied against a Kubuntu 20.04 fresh install.

Installs neuroimaging tools into a quarantine, along with ubuntu dependencies
- minc-toolkit-v2 + extras
- FSL
- freesurfer
- afni
- miniforge (anaconda) with lots of extras
- smaller neuroimaging tools (dcm2niix, mricron, mricrogl, mi-brain)
- resources
- R and all available r packages from cran2deb ppa
- rstudio
- docker + singularity

## Customization

### Tags

Customize install by skipping tags (all tags installed by default):
```sh
$ ansible-playbook --list-tags deploy.yml

playbook: deploy.yml

  play #1 (workstations): workstations  TAGS: []
      TASK TAGS: [R, afni, ants, cobralab, containers, files, freesurfer, fsl, minc, python, resources, science, software]
$ ansible-playbook --skip-tags freesurfer
```

### R packages
The default R package list is in ``files/r-list`` and is *all* functioning cran2deb packages on the CRAN ppa.
A minimum set of packages which supports other third-party R packages is in ``files/r-short-list``, edit
``roles/tasks/R.yml`` to change which list is used.
