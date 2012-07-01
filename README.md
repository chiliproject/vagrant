# chiliproject-vagrant

Try to build a Vagrant environment for ChiliProject development, maybe
deployments too.

The default configuration will setup a PostgreSQL server, Apache + Passenger
and a single ChiliProject instance.

You can customize the instance in `data_bags/chiliproject/default.json`.
Please refer to [the documentation of the chiliproject
cookbook](https://github.com/meineerde/chiliproject-cookbook/blob/master/README.md)
for configuration details.

If you use this repository as a basis for a production deployment, you **HAVE
TO** adapt the configuration and change the secret keys and passwords.

## Usage

    # Install required gems
    bundle install

    # Retrieve cookbooks
    librarian-chef install

    # start the Vagrant VM
    vagrant up

## Known issues

* The current config requires `chili.dev` to point to your `localhost`
* The networking section generally needs more work

## Contributors

* [Felix](https://github.com/thegcat)
* [Holger](https://github.com/meineerde)

## License

Copyright (c) 2012 - Felix Schäfer, Holger Just

This software is licensed under the MIT license. See LICENSE for details.
