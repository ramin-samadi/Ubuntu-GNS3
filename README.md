#!/bin/bash
# Ubuntu GNS3 Installation Script
# This script installs GNS3 and its dependencies on Ubuntu

# Update and upgrade system packages
sudo apt update -y && sudo apt upgrade -y

# Install required virtualization packages
sudo apt install -y qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils virt-manager

# Add GNS3 PPA repository
sudo add-apt-repository -y ppa:gns3/ppa

# Update package list again after adding new repository
sudo apt update

# Install GNS3 GUI and server
sudo apt install -y gns3-gui gns3-server

# Enable support for IOU (IOS on Unix) by adding i386 architecture
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install -y gns3-iou

# Add current user to necessary groups for GNS3
sudo usermod -aG ubridge,libvirt,kvm,wireshark $(whoami)

# Reboot to apply group changes
sudo reboot
