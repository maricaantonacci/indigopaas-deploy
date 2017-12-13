Role Name
=========

This role allows to deploy the INDIGO IAM service.

Requirements
------------

If you want to enable Google Auth you need to create a new client:

Google need to trust in requester application to work with. To do so, you need to access to Google developers console and create and configure a new credential project.
Go to: https://console.developers.google.com/apis/credentials
Create Credentials > OAuth Client ID
Application Type: Web Application
Name: Service Provider (SP) name
Let's assume that our server is iam.com:
Authorized JavaScript origins: https://iam.example.com.
Authorized redirect URIs: https://iam.example.com/openid_connect_login. Keep that in mind.
Copy client ID and client secret. You will need them for configuration.

JSON web keys generation:

<code>
git clone https://github.com/mitreid-connect/json-web-key-generator 
cd json-web-key-generator
docker run --rm -it -v $(pwd):/project -w /project maven mvn package && java -jar target/json-web-key-generator-0.4-SNAPSHOT-jar-with-dependencies.jar   -t RSA -s 1024 -S -i rsa1 -o keys
</code>

References:
https://iam-docs.gitbooks.io/iam-documentation/content/v/develop/admin-guide/json_web_key.html




Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
