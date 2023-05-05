
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
        string(name: 'PERSON', defaultValue: 'MAJIYUE', description: '名字')
        choice(name: 'Branch', choices: [' ', 'master', 'develop', 'users/majiyue/radar_log'], description: '')
        booleanParam(name: 'Publish', defaultValue: 'false', description: '正式发布版?')
    }
            
    stages {
        stage('拉取代码中。。。。。') {
            steps {
                echo "Hello ${params.PERSON}"
                sh "pwd"
                sh "cd .."
                deleteDir()
                echo "是否是正式发布版？${params.Publish}"
                echo "Branch is ${params.Branch}" // Fix here: Use ${params.Branch} or $params.Branch
                
                sh '''
                    git clone https://A23123:!mjy0123456!@adasgitlab.autel.com/tools/cuav_server2.git
                    pwd
                    cd ./cuav_server2
                    pwd
                    git fetch
                    git reset --hard HEAD
                    pwd
                    git checkout ${params.Branch} // Fix here: Use ${params.Branch} or $params.Branch
                '''
            }
        }
    }
// 		stage('gradleInfo') {
// 			steps{
// 			script{
//                         mytools.Printf("应用打包",'green')
// 
// 			gradleHome =tool "gradletool"
//                         mytools.Printf("gradleHome",'green')
// 
// 			sh "${gradleHome}/bin/gradle -version"
// 					}
// 				}
// 		}
    
}


