# Practices-circle-ci
this repo is for practices the new tool relate CI process and better that Jenkins 
Circle- CI  this tool now gaining popularity lot of the company no shifting there CI part from JENKINS  to CIRCLE-CI 


why circle -ci 

the problem face during jenkins is  to setup the server and maintain the server this our job and this increase the extra workload to manage our coustome server and download the jenkins and maintain the version 


Circle -CI server side is maintain by the company no need to track the verison and server launch and installation that why it is the fastest industrial method current in market 

using circle -ci our task is only to intergrate the server with ci process and also code githhub repo . for that  only our task is to login circle-ci with github it will automaticaly intergrate github & circle-ci 

==============================================================================================
github (pythoncode)=>Circle-CI (build-> test->deploy)

the project work flow is (as per devops engineer)
  
	developer will provide the github repo and in that  they will provide
		main.py
		test.py	
		readme.md
          

 but for the devops process we need CONFIG.YML this file is create by devops engineer to give the workflow to circle-ci application 

	steps 1; go to github repo  create folder " .circleci"
		
	step 2: then in this folder create " config.yml"	

" config.yml"	
		{

		version: 2.1
	/* jobs is first created and after that we define workflow */	
		jobs:
		    build:
			 docker:         
				-image : cimg/python:3.11
			 steps :
 			        -checkout
			        -run : python main.py
		
		    test:
			 docker:         
				-image : cimg/python:3.11
			 steps :
 			        -checkout
			        -run : python tests.py
		
		    deploy:
			 docker:         
				-image : cimg/python:3.11
			 steps :
 			 
			        -run : echo"Deployment step for project"


	  	workflow:
			buid_and_test_and_deploy:
				jobs:
				   -build
				   -test :
					requires:
						-build
				   -deploy :
					requires:
						-test
					filters:
					     branches:
						only: main 
					

	}

now this file is create and commit this file in github repo 

after commit this file in github repo the job will automaticaly trigeer 

   
 In background 
		
		-spin up enviroment 
		-preparing enviroment variables
		-checkout code
		-python main.py 


this steps happens in background this very fast tool jenkins and easy to used 


