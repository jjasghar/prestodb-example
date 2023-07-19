# PrestoDB Vagrant env

## Scope

This is a simple 3 node cluster to show off PrestoDB working. There is a [prestodb][prestodb] instance
that connects to a `mariadb` and `redis` instance.

The idea is to be able to show off how a _non_-containerized instance of prestodb would be set up.

## Preqs
- [vagrant][vagrant]
- [Virtualbox][virtualbox] - **note**: this was only tested with Virtualbox

## Usage

- Clone down this repository.
- Verify `vagrant` is working
- Run: `vagrant up`
- When completed `vagrant ssh presto`
- Everything (at this time) is ran as root, so you'll need to `sudo su -`
- The software is installed in `/opt/presto`
- Have fun!

## mysql remote access

I have set up the `remote` user with the password of `123456` on the `mariadb` server.
Right now you can test from `presto` with something like the following:
```bash
mysql -u remote -h 192.168.56.6 -p
> use testdb;
> show tables;
> select * from test;
```

## redis remote access

I have set up the `redis` on the `redis` server.
Right now you can test from `presto` with something like the following:
```bash
redis-cli -h 192.168.56.5
redis>
```
## License & Authors

If you would like to see the detailed LICENSE click [here](./LICENSE).

- Author: JJ Asghar <awesome@ibm.com>

```text
Copyright:: 2023- IBM, Inc

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

[prestodb]: https://github.com/prestodb/presto
[vagrant]: https://www.vagrantup.com
[virtualbox]: https://www.virtualbox.org
