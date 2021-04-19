<h1 align="center">
  <br>
  <a href="https://phoenixnap.com/bare-metal-cloud"><img src="https://user-images.githubusercontent.com/78744488/109779287-16da8600-7c06-11eb-81a1-97bf44983d33.png" alt="phoenixnap Bare Metal Cloud" width="300"></a>
  <br>
  BMC Puppet Module
  <br>
</h1>

<p align="center">
BMC Puppet Module for provisioning and managing <a href="https://phoenixnap.com/bare-metal-cloud">Bare Metal Cloud</a> resources.
</p>

<p align="center">
  <a href="https://phoenixnap.com/bare-metal-cloud">Bare Metal Cloud</a> •
  <a href="https://developers.phoenixnap.com/">Developers Portal</a> •
  <a href="http://phoenixnap.com/kb">Knowledge Base</a> •
  <a href="https://developers.phoenixnap.com/support">Support</a>
</p>

## Requirements

- [Bare Metal Cloud](https://bmc.phoenixnap.com) account
- Ruby
- BMC Ruby SDK

## Creating a Bare Metal Cloud account

1. Go to the [Bare Metal Cloud signup page](https://support.phoenixnap.com/wap-jpost3/bmcSignup).
2. Follow the prompts to set up your account.
3. Use your credentials to [log in to Bare Metal Cloud portal](https://bmc.phoenixnap.com).

:arrow_forward: **Video tutorial:** [How to Create a Bare Metal Cloud Account](https://www.youtube.com/watch?v=RLRQOisEB-k)
<br>

:arrow_forward: **Video tutorial:** [Introduction to Bare Metal Cloud](https://www.youtube.com/watch?v=8TLsqgLDMN4)

## Before installing

Make sure you have installed the BMC Ruby SDK

```sh
/opt/puppetlabs/puppet/bin/gem install bmc-sdk
```

## Installing the module

The module is available to install through Puppet Forge:

```sh
puppet module install phoenixnap-bmc
```

## Authentication

You need to create a configuration file called `config` and save it in the user home directory. This file is used to authenticate access to your Bare Metal Cloud resources.

In your home directory, create a directory `.pnap` and a `config` file inside it. The file needs to contain only two lines of code:

```yml
    client_id: <enter your client id>
    client_secret: <enter your client secret>
```

To get the values for the clientId and clientSecret, follow these steps:

1. [Log in to the Bare Metal Cloud portal](https://bmc.phoenixnap.com).
2. On the left side menu, click on API Credentials.
3. Click the Create Credentials button.
4. Fill in the Name and Description fields, select the permissions scope and click Create.
5. In the table, click on Actions and select View Credentials from the dropdown.
6. Copy the values from the Client ID and Client Secret fields into your `config` file.

## Module Usage

### Creating Bare Metal Instances

The minimal setup for an insntace is

```puppet
pnap_server { 'puppet':
  ensure   => present,
  os       => 'ubuntu/bionic',
  type     => 's1.c1.medium',
  location => 'PHX',
  ssh_keys => [file('/home/<USERNAME>/.ssh/id_rsa.pub')]
}
```

Applying a Puppet manifest which contains the snippet above will create a BMC server instance named `puppet` in the `PHX` data center using the `ubuntu/bionic` image with size `s1.c1.medium` and will use a ssh key from your home directory as the default ssh key.

Keep in mind that if you already have a default ssh key on your account, you don't have to setup ssh keys on the new instance, the default one will automatically be installed so the `ssh_keys/ssh_key_ids` param can be removed or replaced with `install_default_ssh_keys` and set to `true` (this is a default setting).

### Listing Bare Metal Instances

This module supports listing instances via

``` shell
puppet resource pnap_server
```

or you can display a single instance using

```shell
puppet resource pnap_server <name of instance>
```

## Running Tasks

TBD

## Bare Metal Cloud community

Become part of the Bare Metal Cloud community to get updates on new features, help us improve the platform, and engage with developers and other users.

- Follow [@phoenixNAP on Twitter](https://twitter.com/phoenixnap)
- Join the [official Slack channel](https://phoenixnap.slack.com)
- Sign up for our [Developers Monthly newsletter](https://phoenixnap.com/developers-monthly-newsletter)

### Resources

- [Product page](https://phoenixnap.com/bare-metal-cloud)
- [Instance pricing](https://phoenixnap.com/bare-metal-cloud/instances)
- [YouTube tutorials](https://www.youtube.com/watch?v=8TLsqgLDMN4&list=PLWcrQnFWd54WwkHM0oPpR1BrAhxlsy1Rc&ab_channel=PhoenixNAPGlobalITServices)
- [Developers Portal](https://developers.phoenixnap.com)
- [Knowledge Base](https://phoenixnap.com/kb)
- [Blog](https:/phoenixnap.com/blog)

### Documentation

- [API documentation](https://developers.phoenixnap.com/docs/bmc/1/overview)

### Contact phoenixNAP

Get in touch with us if you have questions or need help with Bare Metal Cloud.

<p align="left">
  <a href="https://twitter.com/phoenixNAP">Twitter</a> •
  <a href="https://www.facebook.com/phoenixnap">Facebook</a> •
  <a href="https://www.linkedin.com/company/phoenix-nap">LinkedIn</a> •
  <a href="https://www.instagram.com/phoenixnap">Instagram</a> •
  <a href="https://www.youtube.com/user/PhoenixNAPdatacenter">YouTube</a> •
  <a href="https://developers.phoenixnap.com/support">Email</a> 
</p>

<p align="center">
  <br>
  <a href="https://phoenixnap.com/bare-metal-cloud"><img src="https://user-images.githubusercontent.com/78744488/109779474-47222480-7c06-11eb-8ed6-91e28af3a79c.jpg" alt="phoenixnap Bare Metal Cloud"></a>
</p>