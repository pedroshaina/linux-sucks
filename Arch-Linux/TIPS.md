# Tips using Arch Linux

### Pacman usage
pacman -Sy       # synchronize repository databases if neccessary
pacman -Syy      # force synchronization of repository databases

pacman -Ss xyz   # search repository database for packages for xyz

pacman -S xyz    # install package xyz
pacman -Sy xyz   # synchronize repo and install xyz
pacman -Syy xyz  # really synchronize repo and install xyz

pacman -R xyz    # remove package xyz but keep its dependencies installed
pacman -Rs xyz   # remove package xyz and all its dependencies (if they are not required by any other package)
pacman -Rsc xyz  # remove package xyz, all its dependencies and packages that depend on the target package

pacman -Ql xyz   # show all files installed by the package xyz
pacman -Qo /path # find the package which installed the file at /pat