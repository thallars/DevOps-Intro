# Lab 2 — Version Control & Advanced Git

## Task 1 — Git Object Model Exploration

## 1.1 Sample commits

```bash
thallars@ASUS-TUF:~/Documents/DevOps-Intro$ git status
On branch feature/lab2
nothing to commit, working tree clean
thallars@ASUS-TUF:~/Documents/DevOps-Intro$ echo "Test content" > test.txt
thallars@ASUS-TUF:~/Documents/DevOps-Intro$ git add test.txt
thallars@ASUS-TUF:~/Documents/DevOps-Intro$ git commit -m "Add test file"
[feature/lab2 24dc484] Add test file
 1 file changed, 1 insertion(+)
 create mode 100644 test.txt
```

## 1.2 Inspect Git Objects

### Command outputs and examples

```bash
thallars@ASUS-TUF:~/Documents/DevOps-Intro$ git cat-file -p 2eec599 # blob for test.txt
Test content

thallars@ASUS-TUF:~/Documents/DevOps-Intro$ git cat-file -p 560d532 # tree
040000 tree 427b12c6e48e802d5f39053d3dbab402f8ae374b    .github
100644 blob 6e60bebec0724892a7c82c52183d0a7b467cb6bb    README.md
040000 tree a1061247fd38ef2a568735939f86af7b1000f83c    app
040000 tree eb79e5a468ab89b024bd4f3ed867c6a3954fe1f0    labs
040000 tree d3fb3722b7a867a83efde73c57c49b5ab3e62c63    lectures
100644 blob 2eec599a1130d2ff231309bb776d1989b97c6ab2    test.txt

thallars@ASUS-TUF:~/Documents/DevOps-Intro$ git cat-file -p 24dc484 # commit
tree 560d532e2f9a7e92ed1c5760c05e6ac2228eebd1
parent 5e57782fbef6c6d2e5bd2ee3080e4aaef103bf80
author thallars <arszemlyanikin@gmail.com> 1771057219 +0300
committer thallars <arszemlyanikin@gmail.com> 1771057219 +0300
gpgsig -----BEGIN SSH SIGNATURE-----
 U1NIU0lHAAAAAQAAADMAAAALc3NoLWVkMjU1MTkAAAAgMnV12Q66paCVHknJuSdNMKV9go
 GTg92ZAjIBauGtXIcAAAADZ2l0AAAAAAAAAAZzaGE1MTIAAABTAAAAC3NzaC1lZDI1NTE5
 AAAAQLpCJGfhrCXPlaWXJ3DXqRdHolTvaScqCByP4CCCJMYfaIyP5usulxeQCQFh+TQDex
 7JToppB/HR9jlCXqJYUwM=
 -----END SSH SIGNATURE-----

Add test file
```

### Object types

- Blob (Binary Large Object) stores the content of a file without any metadata.
- Tree represents a directory snapshot, containing references to blobs.
- Commit is a snapshot of the entire repository.

### How Git Stores Repository Data

Git stores data in a key-value database inside the .git/objects directory, where the key is a hash of the content and the value is the compressed object itself.

## Task 2 — Reset and Reflog Recovery