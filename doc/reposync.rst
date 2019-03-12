..
  Copyright (C) 2014  Red Hat, Inc.

  This copyrighted material is made available to anyone wishing to use,
  modify, copy, or redistribute it subject to the terms and conditions of
  the GNU General Public License v.2, or (at your option) any later version.
  This program is distributed in the hope that it will be useful, but WITHOUT
  ANY WARRANTY expressed or implied, including the implied warranties of
  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General
  Public License for more details.  You should have received a copy of the
  GNU General Public License along with this program; if not, write to the
  Free Software Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA
  02110-1301, USA.  Any Red Hat trademarks that are incorporated in the
  source code or documentation are not subject to the GNU General Public
  License and may only be used or replicated with the express permission of
  Red Hat, Inc.

====================
DNF reposync Plugin
====================

Synchronize packages of a remote DNF repository to a local directory.

--------
Synopsis
--------

``dnf reposync [options]``

-----------
Description
-----------

`reposync` makes local copies of remote repositories. Packages that are already present in the local directory are not downloaded again.

-------
Options
-------

``-p <download-path>, --download-path=<download-path>``
    Root path under which the downloaded repositories are stored, relative to the current working directory. Defaults to the current working directory. Every downloaded repository has a subdirectory named after its ID under this path.

``--download-metadata``
    Download all repository metadata. Downloaded copy is instantly usable as a repository, no need to run createrepo_c on it

``-a <architecture>, --arch=<architecture>``
    Download only packages of given architectures (default is all architectures). Can be used multiple times.

``--source``
    Operate on source packages.

``-m, --downloadcomps``
    Also download comps.xml.

``-n, --newest-only``
    Download only newest packages per-repo.

``--delete``
    Delete local packages no longer present in repository

``--metadata-path``
    Root path under which the downloaded metadata are stored. It defaults to ``--download-path`` value if not given.

--------
Examples
--------

This section presents examples of reposync usage and how it combines with generic dnf options.

``dnf reposync --repoid rpmsoftwaremanagement-dnf-nightly -n``
    Synchronizes local directory rpmsoftwaremanagement-dnf-nightly with the newest packages of remote repository with id rpmsoftwaremanagement-dnf-nightly.

``dnf reposync -p repos_dir -n --source``
    Synchronizes newest source packages from all enabled repositories inside directory repos_dir.

``dnf reposync -v --repoid fedora --download-metadata -m``
    Verbosely synchronizes entire fedora repository with metadata, ready to use locally.
