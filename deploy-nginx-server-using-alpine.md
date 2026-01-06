# Deploy Nginx Server using Alpine

#### 1. Pulling the Image Directly

* If you simply want to download the official Nginx image built on Alpine Linux from Docker Hub, use the following command:
* &#x20; `docker pull nginx:alpine`

2\. Creating a Custom `Dockerfile`

> If you want to build your own custom image (for example, to include your own HTML files or configuration) based on Nginx Alpine, create a file named `Dockerfile` with the content below:

<details>

<summary>Use the official Nginx image with the Alpine tag as the base</summary>

<mark style="color:$primary;">Dockerfile</mark>

<mark style="color:$info;">`FROM`</mark>` ``nginx:alpine`

[#optional-copy-static-website-files-from-your-host-to-the-containers-default-html-directory](deploy-nginx-server-using-alpine.md#optional-copy-static-website-files-from-your-host-to-the-containers-default-html-directory "mention")

[#copy-nginx.conf-etc-nginx-nginx.conf-1](deploy-nginx-server-using-alpine.md#copy-nginx.conf-etc-nginx-nginx.conf-1 "mention")

[#optional-copy-static-website-files-from-your-host-to-the-containers-default-html-directory](deploy-nginx-server-using-alpine.md#optional-copy-static-website-files-from-your-host-to-the-containers-default-html-directory "mention")

[#copy-.-html-usr-share-nginx-html](deploy-nginx-server-using-alpine.md#copy-.-html-usr-share-nginx-html "mention")

[#expose-port-80](deploy-nginx-server-using-alpine.md#expose-port-80 "mention")(this is not used to expose the port but to reminder of this app is using the respective port)

<mark style="color:$info;">`EXPOSE`</mark>` `<mark style="color:$warning;">`80`</mark>

[#start-nginx-in-the-foreground](deploy-nginx-server-using-alpine.md#start-nginx-in-the-foreground "mention")

<mark style="color:purple;">`CMD`</mark>` ``[`` `<mark style="color:green;">`"nginx", "-g", "daemon off;"`</mark>`]`

</details>



```
docker build -t my-custom-nginx .
```

#### 3. Running the Container

To run a container using the `nginx:alpine` image (or your custom one) and map port 80 of the container to port 8080 on your host machine:

`docker run -d --name my-nginx-server -p 8080:80 nginx:alpine`

#### Why use the Alpine tag?

* Size: Alpine images are significantly smaller (often around 5MB-10MB base) compared to standard Debian/Ubuntu-based images, which saves storage and speeds up build/deployment times.
* Security: Because it contains fewer packages and libraries, the attack surface is generally smaller.
