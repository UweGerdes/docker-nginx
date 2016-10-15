# Docker uwegerdes/nginx

Make sure you run `uwegerdes/php-fpm` and the other containers before running nginx.

Now run the nginx container, port 3080 on localhost will be connected to the nginx container (change it as you like):

```bash
$ docker run -d \
	-p 3080:80 \
	--volumes-from data \
	--volumes-from php-fpm \
	--name nginx \
	uwegerdes/nginx
```

To use different configuration add the following lines

```bash
	-v $(pwd)/nginx/nginx.conf:/etc/nginx/nginx.conf \
	-v $(pwd)/nginx/sites-enabled/default:/etc/nginx/sites-enabled/default \
```

Useful commands:

```bash
$ docker exec -it nginx tail -f /var/log/nginx/access.log
$ docker exec -it nginx bash
```

Hit CTRL-C to stop the tail command and CTRL-D to exit the bash.

## Open Page

Open [http://localhost:3080/](http://localhost:3080/) in your preferred browser - you should see the /htdocs/index.html content. Change the file and reload it.
