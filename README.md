## Build
```
export BASE='/Users/rcrawford/workarea/trek/misc/DVO-2573'
cd ${BASE}/green; docker build -t green .
docker run -p 80:80 -dit --name webGreen green
docker stop webGreen
cd ${BASE}/blue; docker build -t blue .
docker run -p 80:80 -dit --name webBlue blue
```

## Destroy:
```
docker stop webGreen
docker stop webBlue
docker rm $(docker ps -a -q)
docker rmi -f $(docker images -q)
```

## Toggle:
### Turn on webBlue
```
RESULT=`ssh localhost "/usr/local/bin/docker stop webBlue && /usr/local/bin/docker start webGreen"`
if [[ $RESULT =~ webBlue.*webGreen ]]; then 
    echo 0
else 
    echo 1
fi
```

### Turn on webBlue
```
RESULT=`ssh localhost "/usr/local/bin/docker stop webGreen && /usr/local/bin/docker start webBlue"`
if [[ $RESULT =~ webBlue.*webGreen ]]; then 
    echo 0
else 
    echo 1
fi
```