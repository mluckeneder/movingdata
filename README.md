# Moving Data

## Technology overview
**Amazon AWS** is used to host the workflow orchestrator and run the analysis tools.

**PlanetLab** runs simple RESTful web services which receive an image, write it to the disk and retransmit it again. 

## Required tools
### AWS toolkit
To set up the Amazon AWS toolkit, follow the official guide: [http://aws.amazon.com/developertools/351](http://aws.amazon.com/developertools/351) and configure the toolkit with your AWS account credentials.

### PlanetLab
In order to set up the PlanetLab toolkit, follow the official getting started guide: [https://www.planet-lab.org/doc/guides/user](https://www.planet-lab.org/doc/guides/user)


### Python
Install [Python 2.7.3](http://www.python.org), [pip](https://pypi.python.org/pypi/pip) and [virtualenv](http://www.virtualenv.org/en/latest/)

## Setup
### Python
A *virtualenv* is already included with the source - therefore from the root directory of the repository simply run `. ./activate`. This loads the Python environment and will have all necessary dependencies installed.

Then take some time to edit `config.py` and put in your AWS credentials and an API key from [ipinfodb](http://ipinfodb.com/ip_location_api.php).

### AWS
Follow the Amazon AWS console instructions to create a key pair and a security group. The key pair and security group have to be copied to all AWS regions.

Configure the parameters in `script/add_keypair` and then, from the main directory, run `sh scripts/add_keypair`. This will copy the keypair to all regions

Similarly, the command `python script/copy_security_groups.py` can be used to copy all security groups to all AWS regions.

### PlanetLab
The PlanetLab setup files live in `eg/planetlab`. 

The file `eg/planetlab/nodes.txt` contains a list of PlanetLab nodes where the test web service workflows can be executed. When the project was started, a command was used to retrieve this list of nodes from the PlanetLab [comon](http://comon.cs.princeton.edu) service. However, as of March 2013, this service does not respond to requests and thus the list of live nodes cannot be queried anymore. Since PlanetLab nodes tend to go offline, it might be possible that none of the nodes defined in `nodes.txt` work.

The script file `eg/planetlab/pl.sh` is used to control the web services hosted on PlanetLab. 

`sh eg/planetlab/pl.sh deploy` copies the file in `eg/planetlab/cs4098/server.py` to every node defined in `nodes.txt`.

`sh eg/planetlab/pl.sh install` installs the Python dependencies on all nodes.

`sh eg/planetlab/pl.sh start` starts the web service on every node (accessible via HTTP on port 31415).

`sh eg/planetlab/pl.sh stop` stops the web service on every node.



### PlanetLab setup


### Pre-deployer setup


