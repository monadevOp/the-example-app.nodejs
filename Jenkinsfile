pipeline {
    agent  { docker { image 'node:latest'
                     args ' -u root -p 3000:3000'
            }      }
               
    
    
    stages{
        stage ("checkout") {
            steps{
                echo "checkout"
               
                 checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/monadevOp/the-example-app.nodejs.git']]])

                 }
            }
       
        stage ("Install dependencies"){
            steps{
                echo "installing dependencies"
               
              sh "npm i npm@latest -g"
               sh " npm install"
               sh "npm -v"
               sh"node -v"
            }
        }
       
        stage ("Deploy"){
            steps{
                echo "test"
                sh "npm run start:dev & " 
            }
        }
      
      stage ("Test"){
            steps{
                echo "verify"
                sh "curl http://localhost:3000 &" 
            }
        }
        
    
        
    }
        
        
}
