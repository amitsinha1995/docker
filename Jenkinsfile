pipeline {
        agent {
            label {
                label 'built-in' 
                  }
              }
        
        stages {
// I'll create 4 container of httpd image and sync all container with 'docker-volume' where I'll clone my feature branch(Q1/Q2/Q3/Q4).             
             stage ('container-up') {
                 steps {
                     sh "docker run -itdp 81:80 -v /mnt/Q1branch-vol://usr/local/apache2/htdocs --name server1 httpd"
                     sh "docker run -itdp 82:80 -v /mnt/Q2branch-vol://usr/local/apache2/htdocs --name server2 httpd"
                     sh "docker run -itdp 83:80 -v /mnt/Q3branch-vol://usr/local/apache2/htdocs --name server3 httpd"
                     sh "docker run -itdp 84:80 -v /mnt/Q4branch-vol://usr/local/apache2/htdocs --name server4 httpd"
                       }
                                    }

// Cloning Q1branch in server1 container synced docker-volume             
             stage ('Q1branch-clone') {
                 agent {
                     label {
                         label 'built-in'
                         customWorkspace "/mnt/Q1branch-vol"
                           }
                       }
                 steps {
                     sh "rm -rf *"
                     sh "git init"
                     sh "git clone https://github.com/amitsinha1995/docker.git -b Q1branch"
                     sh "chmod 777 *"
                     sh "cp -r index.html server1://usr/local/apache2/htdocs/"
                       }
                                     }
            
// Cloning Q2branch in server2 container synced docker-volume
             stage ('Q2branch-clone') {
                 agent {
                     label {
                         label 'built-in'
                         customWorkspace "/mnt/Q2branch-vol"
                           }
                       }
                 steps {
                     sh "rm -rf *"
                     sh "git init"
                     sh "git clone https://github.com/amitsinha1995/docker.git -b Q2branch"
                     sh "chmod 777 *"
                     sh "cp -r index.html server2://usr/local/apache2/htdocs/"
                       }
                                     }

// Cloning Q3branch in server3 container synced docker-volume
            stage ('Q3branch-clone') {
                 agent {
                     label {
                         label 'built-in'
                         customWorkspace "/mnt/Q3branch-vol"
                           }
                       }
                 steps {
                     sh "rm -rf *"
                     sh "git init"
                     sh "git clone https://github.com/amitsinha1995/docker.git -b Q3branch"
                     sh "chmod 777 *"
                     sh "cp -r index.html server3://usr/local/apache2/htdocs/"
                       }
                                    }

// Cloning Q4branch in server4 container synced docker-volume
           stage ('Q4branch-clone') {
                 agent {
                     label {
                         label 'built-in'
                         customWorkspace "/mnt/Q4branch-vol"
                           }
                       }
                 steps {
                     sh "rm -rf *"
                     sh "git init"
                     sh "git clone https://github.com/amitsinha1995/docker.git -b Q4branch"
                     sh "chmod 777 *"
                     sh "cp -r index.html server4://usr/local/apache2/htdocs/"
                       }
                                    }

            
           }
}
