pipeline {
    agent any
    parameters{
        string(name: 'PERSON', defaultValue: 'MAJIYUE', description: '名字')
        choice(name: 'Branch', choices: [' ', 'master', 'develop', 'users/majiyue/cloud_log',
        'users/luchongyang/feature_plugins','users/luoyi/feature_radar_gun_ota'], description: '')
        booleanParam(name: 'Publish', defaultValue: 'false', description: '正式发布版?')
    }
            
    stages {
        stage('拉取代码中。。。。。') {
            steps {
                echo "Hello ${params.PERSON}"
                sh "pwd"
              
                echo "是否是正式发布版？${params.Publish}"
                echo "Branch is ${params.Branch}"  
                sh """
                    cd /home/go/workspace/
                    rm -rf /home/go/workspace/cuav_server2
                    mkdir cuav_server2
                    cd /home/go/workspace/cuav_server2
                    git clone https://A23123:!mjy0123456!@adasgitlab.autel.com/tools/cuav_server2.git /home/go/workspace/cuav_server2
                 
                    cd /home/go/workspace/cuav_server2
                
                    git fetch
                    git reset --hard HEAD
                    
                    git checkout ${params.Branch}
		            sudo chmod +x /var/jenkins_home/.bash_profile
		            . /var/jenkins_home/.bash_profile	
		            go env -w GO111MODULE=on
                    go env -w GOPROXY=https://goproxy.io,direct
                    go env -w GOPRIVATE=adasgitlab.autel.com
                    export GOPATH=/home/go/workspace
                    go env GOPATH
                    cd ./sdk
                    go install golang.org/x/mobile/cmd/gomobile@latest
                    pwd
                    go mod tidy&&go get golang.org/x/mobile
                    make android
                    rm -rf /home/services.aar
                    cp services.aar /home/
                """
            }
        }
    }
}
