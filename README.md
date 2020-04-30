What's Joomla :-

Joomla is a free and open-source content management system (CMS) for publishing web content. It is built on a model–view–controller web application framework that can be used independently of the CMS. Joomla is written in PHP, uses object-oriented programming (OOP) techniques and software design patterns, stores data in a MySQL, MS SQL, or PostgreSQL database, and includes features such as page caching, RSS feeds, printable versions of pages, news flashes, blogs, search, and support for language internationalization.


How to use this image :-
  $ docker run --name some-joomla --link some-mysql:mysql -d joomla

The following environment variables are also honored for configuring your Joomla instance:

-e JOOMLA_DB_HOST=... (defaults to the IP and port of the linked mysql container)

-e JOOMLA_DB_USER=... (defaults to "root")

-e JOOMLA_DB_PASSWORD=... (defaults to the value of the MYSQL_ROOT_PASSWORD environment variable from the linked mysql container)

-e JOOMLA_DB_NAME=... (defaults to "joomla")

If the JOOMLA_DB_NAME specified does not already exist on the given MySQL server, it will be created automatically upon startup of the joomla container, provided that the JOOMLA_DB_USER specified has the necessary permissions to create it.

If you'd like to be able to access the instance from the host without the container's IP, standard port mappings can be used:

$ docker run --name some-joomla --link some-mysql:mysql -p 8080:80 -d joomla

Then, access it via http://localhost:8080 or http://host-ip:8080 in a browser.

If you'd like to use an external database instead of a linked mysql container, specify the hostname and port with JOOMLA_DB_HOST along with the password in JOOMLA_DB_PASSWORD and the username in JOOMLA_DB_USER (if it is something other than root):

$ docker run --name some-joomla -e JOOMLA_DB_HOST=10.1.2.3:3306 \

    -e JOOMLA_DB_USER=... -e JOOMLA_DB_PASSWORD=... -d joomla

... via docker stack deploy or docker-compose

As given in docker-compose.yml file
