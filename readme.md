instructions for running:
1. clone repo into e.g. ```/my/dir/jmhsite```
2. install docker and docker-compose
3. ```cd /my/dir/jmhsite```
4. ```docker-compose up```
This will 
- build a docker image containing the required gemfiles and whatever for the blog 
- run it, so that it's accessible at localhost:4000 from your browser
- this will attach /my/dir/jmhsite to /blog inside of the container, so that
changes you make are automatically reflected by the running service
- this is useful for blogging locally and testing out how your changes look