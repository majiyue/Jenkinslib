
@Library('mylib') _
def mytools = new org.devops.tools()
 
pipeline {
	agent { label  "build" }
	stages {
		stage("hello"){
			steps{
				script{
                    mytools.Post("success",'green')
				}
			}
		}
	}
