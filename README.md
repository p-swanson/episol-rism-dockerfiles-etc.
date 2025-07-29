# episol-rism-dockerfiles-etc.
Dockerfiles with tini entrypoint. 

When running HTC jobs this is the only method i've found works. must give tini supreaper access and set as entrypoint and allow to kill groups   
```
FROM existing/image_blah_blah

ENV TINI_VERSION=v0.19.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /tini
RUN chmod +rx /tini
ENV TINI_SUBREAPER=true
RUN your_cmd.exe && etc.
ENTRYPOINT ["/tini","-s","-g","--"]
```
