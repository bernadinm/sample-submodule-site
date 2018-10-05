# Example Website Using Versioned Git Submodules

```bash
mesospheres-MacBook-Pro-67:test-submodule mbernadin$ git submodule add git@github.com:dcos/dcos ext/dcos/1.11 -b 1.11
Cloning into '/Users/mbernadin/Sites/test-submodule/ext/dcos/1.11'...
remote: Enumerating objects: 2, done.
remote: Counting objects: 100% (2/2), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 28881 (delta 0), reused 1 (delta 0), pack-reused 28879
Receiving objects: 100% (28881/28881), 6.99 MiB | 7.52 MiB/s, done.
Resolving deltas: 100% (19114/19114), done.
```

```bash
mesospheres-MacBook-Pro-67:test-submodule mbernadin$ ls
docs	ext
```

```bash
mesospheres-MacBook-Pro-67:test-submodule mbernadin$ cd ext/dcos/1.11/
.editorconfig                CHANGES.md                   NEWS                         build_dcos_launch.sh         cloud_images/                dcos_installer/              mergebot-config.json         prep_local                   setup.py                     tox.ini
.git                         Jenkinsfile                  NOTICE                       build_local.sh               config/                      docs/                        owners.json                  prep_local_windows.ps1       ssh/
.github/                     Jenkinsfile-insecure.groovy  PULL_REQUEST_TEMPLATE.md     build_local_windows.ps1      conftest.py                  flake8_dcos_lint/            packages/                    prep_teamcity                symlink_check
.gitignore                   LICENSE                      README.md                    build_teamcity               contributing.md              gen/                         pkgpanda/                    release/                     test_util/
```

```bash
mesospheres-MacBook-Pro-67:test-submodule mbernadin$ git submodule add git@github.com:dcos/dcos ext/dcos/1.12 -b 1.12
Cloning into '/Users/mbernadin/Sites/test-submodule/ext/dcos/1.12'...
remote: Enumerating objects: 2, done.
remote: Counting objects: 100% (2/2), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 28881 (delta 0), reused 1 (delta 0), pack-reused 28879
Receiving objects: 100% (28881/28881), 6.99 MiB | 14.39 MiB/s, done.
Resolving deltas: 100% (19114/19114), done.
```

```bash
[submodule "ext/dcos/1.11"]
	path = ext/dcos/1.11
	url = git@github.com:dcos/dcos
[submodule "ext/dcos/1.12"]
	path = ext/dcos/1.12
	url = git@github.com:dcos/dcos
```

```bash
mesospheres-MacBook-Pro-67:docs mbernadin$ tree .
.
├── dcos-1.11
└── dcos-1.12

2 directories, 0 files
mesospheres-MacBook-Pro-67:docs mbernadin$ ls
dcos-1.11	dcos-1.12
mesospheres-MacBook-Pro-67:docs mbernadin$ cd dcos-1.11/
mesospheres-MacBook-Pro-67:dcos-1.11 mbernadin$ ln -s ../../ext/dcos/1.11/docs docs
mesospheres-MacBook-Pro-67:dcos-1.11 mbernadin$ ls -l
total 0
lrwxr-xr-x  1 mbernadin  staff  24 Oct  4 17:23 docs -> ../../ext/dcos/1.11/docs
```

```bash
mesospheres-MacBook-Pro-67:docs mbernadin$ cd ../dcos-1.12/
mesospheres-MacBook-Pro-67:dcos-1.12 mbernadin$ ln -s ../../ext/dcos/1.12/docs docs
mesospheres-MacBook-Pro-67:dcos-1.12 mbernadin$ ls -l
total 0
lrwxr-xr-x  1 mbernadin  staff  24 Oct  4 17:24 docs -> ../../ext/dcos/1.12/docs
mesospheres-MacBook-Pro-67:dcos-1.12 mbernadin$ cd ..
mesospheres-MacBook-Pro-67:docs mbernadin$ tree .
.
├── dcos-1.11
│   └── docs -> ../../ext/dcos/1.11/docs
└── dcos-1.12
    └── docs -> ../../ext/dcos/1.12/docs

4 directories, 0 files
```

```bash
mesospheres-MacBook-Pro-67:sample-submodule-site mbernadin$ git submodule sync
Synchronizing submodule url for 'ext/dcos/1.11'
Synchronizing submodule url for 'ext/dcos/1.12'
```

