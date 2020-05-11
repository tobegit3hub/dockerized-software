# YAPF Docker

## Introduction

[Yapf](https://github.com/google/yapf) is the best Python code formater by Google Inc. Now you can format your code with yapf-docker without installing anything.

## Usage

Format the code in-place.

```
docker run -v $(pwd):/tmp tobegit3hub/yapf-docker
```

Review what yapf will do.

```
docker run -v $(pwd):/tmp tobegit3hub/yapf-docker yapf -r -d /tmp
```
