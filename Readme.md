Overview
========

Docker image for rdiffweb.

Rdiffweb is used to browse and restore backups created by rdiff-backup. It cannot be used to configure rdiff-backup.

PULL
=======
```docker pull jshridha/rdiffweb:latest```

Building
========

```docker build -t <username>/rdiffweb:<tag>```

Running
=======

This container needs access to a minimum of three external volumes.
/etc/rdiffweb is used as persistent store for the rdiffweb settings.
/backups is the location where rdiff-backup stores its backups.
/restores is the location where backups should be restored.

**Example**: Run without persistent storage or access to backups/restores
```
docker run -d --name=rdiffweb -p 8080:8080 jshridha/rdiffweb:latest
```

**Example**: Run with persistent storage and access to backups/restores
```
docker run -d --name=rdiffweb -p 8080:8080 -v /docker/rdiffweb/config:/etc/rdiffweb -v /var/backups:/backups -v /var/restores:/restores jshridha/rdiffweb:latest
```

Access
=======
Access the web UI by browsing to http://hostname:8080

Default username: admin
Default password: admin123

After going through the initial initializtion steps, go to the admin area to add users and assign backup locations to these users.

Note: Multiple volume mounts can be attached to the container to allow for backups in many locations.

