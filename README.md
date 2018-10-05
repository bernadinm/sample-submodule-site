# Example Website Using Versioned Git Submodules


Here is an example of how a git submodule looks like when doing versioned documentation. 

```bash
mesospheres-MacBook-Pro-67:test-submodule mbernadin$ git submodule add -b 1.11 git@github.com:dcos/dcos ext/dcos/1.11
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
mesospheres-MacBook-Pro-67:test-submodule mbernadin$ git submodule add -b 1.12 git@github.com:dcos/dcos ext/dcos/1.12
Cloning into '/Users/mbernadin/Sites/test-submodule/ext/dcos/1.12'...
remote: Enumerating objects: 2, done.
remote: Counting objects: 100% (2/2), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 28881 (delta 0), reused 1 (delta 0), pack-reused 28879
Receiving objects: 100% (28881/28881), 6.99 MiB | 14.39 MiB/s, done.
Resolving deltas: 100% (19114/19114), done.
```

```bash
[submodule "ext/dcos/1.12"]
	path = ext/dcos/1.12
	url = git@github.com:dcos/dcos
	branch = 1.12
[submodule "ext/dcos/1.11"]
	path = ext/dcos/1.11
	url = git@github.com:dcos/dcos
	branch = 1.11
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

```bash
mesospheres-MacBook-Pro-67:sample-submodule-site mbernadin$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   .gitmodules
	new file:   README.md
	new file:   docs/dcos-1.11/docs
	new file:   docs/dcos-1.12/docs
	new file:   ext/dcos/1.11
	new file:   ext/dcos/1.12
```

```bash
mesospheres-MacBook-Pro-67:sample-submodule-site mbernadin$ git commit -m "hello world docs"
[master (root-commit) 58187b6] hello world docs
 6 files changed, 95 insertions(+)
 create mode 100644 .gitmodules
 create mode 100644 README.md
 create mode 120000 docs/dcos-1.11/docs
 create mode 120000 docs/dcos-1.12/docs
 create mode 160000 ext/dcos/1.11
 create mode 160000 ext/dcos/1.12
mesospheres-MacBook-Pro-67:sample-submodule-site mbernadin$ git push origin master
Enumerating objects: 11, done.
Counting objects: 100% (11/11), done.
Delta compression using up to 8 threads.
Compressing objects: 100% (6/6), done.
Writing objects: 100% (11/11), 2.28 KiB | 2.28 MiB/s, done.
Total 11 (delta 0), reused 0 (delta 0)
remote:
remote: Create a pull request for 'master' on GitHub by visiting:
remote:      https://github.com/bernadinm/sample-submodule-site/pull/new/master
remote:
To github.com:bernadinm/sample-submodule-site.git
 * [new branch]      master -> master
```
