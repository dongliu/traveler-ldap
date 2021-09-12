# traveler-ldap
openladp docker container for traveler development

## The base docker images

https://github.com/osixia/docker-openldap
and https://github.com/osixia/docker-phpLDAPadmin

## Usage

Clone this repo to your local environment. Make sure you have the `traveler-dev` network in the docker.
```
docker network list
```

If not, run the following in your console to create the network.

```
docker network create -d bridge --subnet 172.18.1.0/24 traveler-dev
```

run `docker-compose up` to start the containers. The images will be downloaded and initialize for the first time run.

You can check the state of the openladp service via the php ldap admin web
<https://localhost:6443> .

There is a default admin account that you can use to log in
user name: `cn=admin,dc=example,dc=org`
password: `admin`

This admin account will also be used by traveler for ldap interactions.

You can add or modify user records in the web interface easily.

The `seed/traveler.ldif` file will be loaded by the `slapd` when it starts.

You can find the initial users including their uid and password in `seed/traveler.ldif`. Those users are available when the tranveler service uses the ldap service on the docker instance for authentication. You can add more users in the `traveler.ldif` file for testing.
