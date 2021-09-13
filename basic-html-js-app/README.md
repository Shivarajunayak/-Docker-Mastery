# Steps to containerize the app


#### Step 1
```docker build -t first-docker-app .```

#### Step 2
```docker container run --name=first-docker-cont -d -p 8000:80 first-docker-app```

#### Now
Simply write ```localhost:8000``` or write ```http://localhost:8000``` in your browser.


<i><b>Note</b>: You need to be in the ```basic-html-js-app``` directory in order to execute the above statements. 
</i>


