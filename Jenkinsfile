
@Library('mylib') _
def mytools = new org.devops.tools()
 
// pipeline {
// 	agent any
// 	stages {
// 		stage("hello"){
// 			steps{
// 				script{
//                     mytools.Printf("success",'green')
// 				}
// 			}
// 		}
// 	}
// }

pipeline {
    agent any
    parameters{	   
                    string(name:'PERSON',defaultValue:'MAJIYUE',description:'名字')
                    choice(name: 'Branch', choices: [' ', 'master', 'develop','user/majiyue/radar_log'], description: '')
                    booleanParam(name: 'Publish', defaultValue: 'false', description: '正式发布版?')
            }
    stages {
        stage('Hello') {
            steps {
                echo "Branch is ${Branch}"
                echo "Hello ${params.PERSON}"
		echo "是否是正式发布版？&{params.Publish}"
		
            }
        }
		stage('gradleInfo') {
			steps{
			script{
                        mytools.Printf("应用打包",'green')

			gradleHome =tool "gradletool"
                        mytools.Printf("gradleHome",'green')
						
			sh "${gradleHome}/bin/gradle -version"
					}
				}
		}
    }
}

