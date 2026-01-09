# Docker container issue

1. Check if the container's volume **`/usr/local/apache2/htdocs`** is correctly mapped with the host's volume **`/var/www/html`**.<br>

use  **`docker inspect <container_name_or_id> -f '{{ json .Mounts }}'`  &#x20;**&#x20;

to check for the source and destination mapped or not
