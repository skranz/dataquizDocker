Docker container for a dataquiz shinyapp (see https://github.com/skranz/dataquiz)

Theis image is essentially build upon `rocker/tidyverse` using my intermediate image `skranz/rskranz` that installs some R packages commonly used by me.

Here is a sample docker run command that runs the shiny app on port 7001 and has no RStudio server access to the container. To open RStudio server access see the example run commands for rocker/rstudio.

```
docker run -entrypoint="/usr/bin/with-contenv bash" --name dataquiz -d -p 7001:3838  -v <shinyapp-dir-on-host>:/srv/shiny-server/ -v <quizdir-on-host>:/srv/quizdir skranz/dataquiz
```

For the shinyapp and quiz directories that you need to place on your host, you can use the `app` and `quizdir` directories provided on https://github.com/skranz/dataquizResources. You must copy them to some directory on your host and adapt the directories in the docker run command above.


