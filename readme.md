# Guide to setup the homeserver from scratch

## calibre-web
```yml
    calibre-web:
        image: lscr.io/linuxserver/calibre-web:amd64-latest
        container_name: calibre-web
        environment:
            - PUID=1000
            - PGID=1000
            - TZ=Asia/Calcutta
            - DOCKER_MODS=linuxserver/calibre-web:calibre
            - OAUTHLIB_RELAX_TOKEN_SCOPE=1
        volumes:
            - ./calibre_data/config:/config
            - ./calibre_data/books:/books
        ports:
            - 2000:8083
        restart: unless-stopped
```

- Documentation for this docker image: [](https://docs.linuxserver.io/images/docker-calibre-web)
- Use the image 'amd64-latest' to get the `ebook-convert` tools.
- Change admin credentials. Default admin credentials are:
    - Username: admin
    - Password: admin123
- Switch to dark theme in the settings.
- Admin is allowed to add users.
- Admin cannot "read" the books, have to access from a user account for that.
- Allow guest to browser books.
- Allow users to upload books.
- Allow users to read books.
- Allow users to download books.
- Set the path for the `ebook-convert` binary: `/usr/bin/ebook-convert`.
- Set the path for the `unrar` binary: `/usr/bin/unrar`.
- To convert books you'll, have to select the book, then go to edit metadata option and there you will find the option to convert the format of the book.
