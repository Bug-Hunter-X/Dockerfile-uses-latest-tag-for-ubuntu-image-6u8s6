# Dockerfile Bug: Using 'latest' tag

This repository demonstrates a common but problematic practice in Dockerfiles: using the `latest` tag for base images.  The `ubuntu:latest` image is not pinned to a specific version, so builds might break unexpectedly due to changes in the base image. This can lead to inconsistent behavior and deployment issues.

The provided `Dockerfile` shows the problematic code. The `Dockerfile-solution` shows the corrected version, demonstrating how to specify a particular ubuntu version to maintain reproducibility and stability.

## How to reproduce:

1. Clone this repo.
2. Build the original Dockerfile: `docker build -t buggy-app -f Dockerfile .`
3. Attempt to run the image: `docker run buggy-app`
4. Build the corrected Dockerfile: `docker build -t stable-app -f Dockerfile-solution .`
5. Run the corrected image: `docker run stable-app`

Note the potential for breakage in step 3 if the ubuntu:latest image is updated in the future, while step 5 guarantees consistent behavior.