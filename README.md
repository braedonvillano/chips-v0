
# [Elastic Beanstalk](http://aws.amazon.com/elasticbeanstalk/) [Docker](https://www.docker.com/) [Node.js](https://nodejs.org/) Example

Example of developing and deploying a [dockerized]((https://www.docker.com/)) [Node.js](https://nodejs.org/) app to [Elastic Beanstalk](http://aws.amazon.com/elasticbeanstalk/)

## Local Development Workflow

1. Edit code. e.g. `index.js`
2. Build image

	```bash
	$ docker build --tag="pfeilbr/eb-docker-node-example" .
	```

3. Run

	```bash
	$ docker run -p 80:80 -it -rm -name eb-docker-node-example pfeilbr/eb-docker-node-example
	```

4. Get docker host ip *(optional.  only if using [boot2docker](http://boot2docker.io/))*

	```bash
	$ boot2docker ip
	```

5. Open browser to `http://<boot2docker ip>`

## Initial Deployment

1. Init git repo

	```bash
	$ git init .
	```

2. Add files to repo 

	```bash
	$ git add .
	```

3. Commit changes

	```bash
	$ git commit -m "init"
	```

4. Create eb app

	```bash
	$ eb init # populate details
	```

	> Populate all details

5. Create environment for app

	```bash
	$ eb create dev-env
	```

	> **IMPORTANT** Must immediately update the ec2 instance with tags so it doesn't get terminated.  Enable termination protection on the ec2 instance.

**Output**

![](http://note.io/1ETb45Y)


## Deploying Updates

1. Modify code and test via [Local Development Workflow]
2. Commit changes

	```bash
	$ git commit -a -m "my updates"
	```

3. Deploy to eb

	```bash
	$ eb deploy
	```

> NOTE: Takes between 3-5 min to deploy changes

**Output**

![](http://note.io/1FFQXuL)