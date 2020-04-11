[![Release](https://img.shields.io/github/v/release/bloodhunterd/froxlor-mail-spamassassin-docker?include_prereleases&style=for-the-badge)](https://github.com/bloodhunterd/froxlor-mail-spamassassin-docker/releases)
[![Docker Build](https://img.shields.io/docker/cloud/build/bloodhunterd/froxlor-mail-spamassassin?style=for-the-badge)](https://hub.docker.com/r/bloodhunterd/froxlor-mail-spamassassin)
[![License](https://img.shields.io/github/license/bloodhunterd/froxlor-mail-spamassassin-docker?style=for-the-badge)](https://github.com/bloodhunterd/froxlor-mail-spamassassin-docker/blob/master/LICENSE)

# SpamAssassin for Froxlor Mail

Docker Image of SpamAssassin for Froxlor Mail Server.

## Configuration

See example [Docker Compose file](https://github.com/bloodhunterd/froxlor-mail-spamassassin-docker/blob/master/docker-compose.yml).

### Environment

| ENV | Values¹ | Default | Description
|--- |--- |--- | ---
| TZ | [PHP: List of supported timezones - Manual](https://www.php.net/manual/en/timezones.php) | Europe/Berlin | Timezone.
| MAIL_DIR | *Directory path* | /var/customers/mail | Absolute path to the mail directory
| REPORT_SAFE | 0 / 2 | 0 | Save Spam message as attachment instead of modifying
| REQUIRED_SCORE | 0.0 - ... | 3.0 | Threshold at which a message is considered spam
| TRUSTED_NETWORKS | *FQDN / IP* | 127.0.0.1 | Trusted networks or hosts

¹ *Possible values are separated by a slash or a range is indicated by a dash.*

### Volumes

```bash
volumes:
  - ./mail/:/var/customers/mail/
```

### Scheduled tasks

Add the following lines to the host [crontab](https://www.linuxwiki.de/crontab), to learn SpamAssassin based on Inbox and Spam folders.

```bash
# Learn SpamAssassin
0 4 * * * /usr/bin/docker exec froxlor-mail-spamassassin /bin/bash -c '/srv/learn.sh'
```

## Update

Please note the [changelog](https://github.com/bloodhunterd/froxlor-mail-spamassassin-docker/blob/master/CHANGELOG.md) to check for configuration changes before updating.

## Build With

* [SpamAssassin](https://spamassassin.apache.org/)
* [Debian](https://www.debian.org/)
* [Docker](https://www.docker.com/)

## Authors

* [BloodhunterD](https://github.com/bloodhunterd)

## License

This project is licensed under the Unlicense - see [LICENSE.md](https://github.com/bloodhunterd/froxlor-mail-spamassassin-docker/blob/master/LICENSE) file for details.
