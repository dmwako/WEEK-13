|---|
| :- |
||- name: Config Web VM with Docker|
||`  `hosts: webservers|
||`  `become: true|
||`  `tasks:|
||`    `- name: docker.io|
||`      `apt:|
||`        `update\_cache: yes|
||`        `name: docker.io|
||`        `state: present|
||<p></p><p></p>|
||`    `- name: Install pip3|
||`      `apt:|
||`        `name: python3-pip|
||`        `state: present|
||<p></p><p></p>|
||`    `- name: Install Docker python module|
||`      `pip:|
||`        `name: docker|
||`        `state: present|
||<p></p><p></p>|
||`    `- name: download and launch a docker web container|
||`      `docker\_container:|
||`        `name: dvwa|
||`        `image: cyberxsecurity/dvwa|
||`        `state: started|
||`        `restart\_policy: always|
||`        `published\_ports: 80:80|
||<p></p><p></p>|
||`    `- name: Enable docker service|
||`      `systemd:|
||`        `name: docker|
||`        `enabled: yes|

