
@Library('mylib') _
def mytools = new org.deveops.tools()
 
pipeline {
	agent any
	stages {
		stage("hello"){
			steps{
				script{
                    mytools.Printf("success",'green')
				}
			}
		}
	}
}
