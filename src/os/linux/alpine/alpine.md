# Alpine

## apk

## apk --help

```text
apk-tools 2.10.4, compiled for x86_64.

Installing and removing packages:
  add       Add PACKAGEs to 'world' and install (or upgrade) them, while ensuring that all dependencies are met
  del       Remove PACKAGEs from 'world' and uninstall them

System maintenance:
  fix       Repair package or upgrade it without modifying main dependencies
  update    Update repository indexes from all remote repositories
  upgrade   Upgrade currently installed packages to match repositories
  cache     Download missing PACKAGEs to cache and/or delete unneeded files from cache

Querying information about packages:
  info      Give detailed information about PACKAGEs or repositories
  list      List packages by PATTERN and other criteria
  dot       Generate graphviz graphs
  policy    Show repository policy for packages

Repository maintenance:
  index     Create repository index file from FILEs
  fetch     Download PACKAGEs from global repositories to a local directory
  verify    Verify package integrity and signature
  manifest  Show checksums of package contents

Use apk <command> --help for command-specific help.
Use apk --help --verbose for a full command listing.
```

## apk --help --verbose

```text
apk-tools 2.10.4, compiled for x86_64.

usage: apk COMMAND [-h|--help] [-p|--root DIR] [-X|--repository REPO] [-q|--quiet] [-v|--verbose] [-i|--interactive]
           [-V|--version] [-f|--force] [--force-binary-stdout] [--force-broken-world] [--force-non-repository]
           [--force-old-apk] [--force-overwrite] [--force-refresh] [-U|--update-cache] [--progress] [--progress-fd FD]
           [--no-progress] [--purge] [--allow-untrusted] [--wait TIME] [--keys-dir KEYSDIR]
           [--repositories-file REPOFILE] [--no-network] [--no-cache] [--cache-dir CACHEDIR] [--cache-max-age AGE]
           [--arch ARCH] [--print-arch] [ARGS]...

The following commands are available:
  add       Add PACKAGEs to 'world' and install (or upgrade) them, while ensuring that all dependencies are met
  del       Remove PACKAGEs from 'world' and uninstall them
  fix       Repair package or upgrade it without modifying main dependencies
  update    Update repository indexes from all remote repositories
  info      Give detailed information about PACKAGEs or repositories
  list      List packages by PATTERN and other criteria
  search    Search package by PATTERNs or by indexed dependencies
  upgrade   Upgrade currently installed packages to match repositories
  cache     Download missing PACKAGEs to cache and/or delete unneeded files from cache
  version   Compare package versions (in installed database vs. available) or do tests on literal version strings
  index     Create repository index file from FILEs
  fetch     Download PACKAGEs from global repositories to a local directory
  audit     Audit the directories for changes
  verify    Verify package integrity and signature
  dot       Generate graphviz graphs
  policy    Show repository policy for packages
  stats     Show statistics about repositories and installations
  manifest  Show checksums of package contents

Global options:
  -h, --help              Show generic help or applet specific help
  -p, --root DIR          Install packages to DIR
  -X, --repository REPO   Use packages from REPO
  -q, --quiet             Print less information
  -v, --verbose           Print more information (can be doubled)
  -i, --interactive       Ask confirmation for certain operations
  -V, --version           Print program version and exit
  -f, --force             Enable selected --force-* (deprecated)
  --force-binary-stdout   Continue even if binary data is to be output
  --force-broken-world    Continue even if 'world' cannot be satisfied
  --force-non-repository  Continue even if packages may be lost on reboot
  --force-old-apk         Continue even if packages use unsupported features
  --force-overwrite       Overwrite files in other packages
  --force-refresh         Do not use cached files (local or from proxy)
  -U, --update-cache      Alias for --cache-max-age 1
  --progress              Show a progress bar
  --progress-fd FD        Write progress to fd
  --no-progress           Disable progress bar even for TTYs
  --purge                 Delete also modified configuration files (pkg removal) and uninstalled packages from cache
                          (cache clean)
  --allow-untrusted       Install packages with untrusted signature or no signature
  --wait TIME             Wait for TIME seconds to get an exclusive repository lock before failing
  --keys-dir KEYSDIR      Override directory of trusted keys
  --repositories-file REPOFILE Override repositories file
  --no-network            Do not use network (cache is still used)
  --no-cache              Do not use any local cache path
  --cache-dir CACHEDIR    Override cache directory
  --cache-max-age AGE     Maximum AGE (in minutes) for index in cache before refresh
  --arch ARCH             Use architecture with --root
  --print-arch            Print default arch and exit

This apk has coffee making abilities.
```
