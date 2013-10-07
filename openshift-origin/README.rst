==========================
OpenShift Origin templates
==========================

This directory contains files for deploying OpenShift Origin to an OpenStack environment via heat.

It includes the following files:

* `F18-x86_64-openshift-origin-broker-cfntools.tdl` - oz template for building a broker image
* `F18-x86_64-openshift-origin-node-cfntools.tdl` - oz template for building a node image
* `OpenShift.template` - heat template for launching OpenShift Origin with a single broker server and a single node server
* `openshift-origin` - diskimage-builder elements to build images, as an alternative to oz

To build with diskimage-builder, do the following in the parent directory of heat-templates::

  yum install -y diskimage-builder
  git clone https://github.com/openstack/tripleo-image-elements.git
  mkdir $HOME/tmp
  export ELEMENTS_PATH=tripleo-image-elements/elements:heat-templates/openshift-origin/elements
  TMP_DIR=$HOME/tmp DIB_IMAGE_SIZE=5 disk-image-create --no-tmpfs -a amd64 vm fedora openshift-origin-broker -o F19-x86_64-openshift-origin-broker-cfntools
  TMP_DIR=$HOME/tmp DIB_IMAGE_SIZE=20 disk-image-create --no-tmpfs -a amd64 vm fedora openshift-origin-node -o F19-x86_64-openshift-origin-node-cfntools

