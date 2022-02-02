
pipeline {
    agent  { docker { image 'node:latest'
                     args ' -u root -p 3000:3000'
                    }  }
               
    
    
    stages {
       
        stage ("checkout") {
            steps{
                echo "checkout"         
                sh "git clone https://github.com/monadevOp/the-example-app.nodejs.git"
                 }
            }
       
        stage ("Install dependencies") {
            steps{
               echo "installing dependencies"             
               sh "npm i npm@latest -g"
               sh " cd the-example-app.nodejs && npm install"
               sh "npm -v"
               sh"node -v"
            }
        }
       
        stage ("Deploy"){
            steps{
                echo "test"
                sh "cd the-example-app.nodejs && npm run start:dev & " 
            }
        }
      
      stage ("Test"){
            steps{
                echo "verify"
                sh "curl http://localhost:3000 &" 
           }
        }
    }
     post { always {
         cleanWs()
          }   
     }     
        
}
