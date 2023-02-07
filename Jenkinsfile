pipeline {
        agent {
            label {
                label 'built-in' 
                  }
              }
        
        stages {
// I'll create 4 container of httpd image and sync all container with 'docker-volume' where I'll clone my feature branch.             
             stage ('container-up') {
                 steps {
                     sh "docker run -itdp 81:80 -v /mnt/23Q1branch-vol://usr/local/apache2/htdocs --name server1 httpd"
                     sh "docker run -itdp 82:80 -v /mnt/23Q2branch-vol://usr/local/apache2/htdocs --name server2 httpd"
                     sh "docker run -itdp 83:80 -v /mnt/23Q3branch-vol://usr/local/apache2/htdocs --name server3 httpd"
                     sh "docker run -itdp 84:80 -v /mnt/23Q4branch-vol://usr/local/apache2/htdocs --name server4 httpd"
                       }
                                    }

// Cloning 23Q1branch in server1 container synced docker volume-23Q1branch-vol            
             stage ('23Q1branch-clone') {
                 agent {
                     label {
                         label 'built-in'
                         customWorkspace "/mnt/23Q1branch-vol"
                           }
                       }
                 steps {
                     sh "rm -rf *"
                     sh "git clone https://github.com/amitsinha1995/docker.git -b 23Q1branch"
                     sh "chmod 777 *"
                     sh "cp -r index.html server1://usr/local/apache2/htdocs/"
                       }
                                     }
            
// Cloning 23Q2branch in server2 container synced docker volume-23Q2branch-vol
             stage ('23Q2branch-clone') {
                 agent {
                     label {
                         label 'built-in'
                         customWorkspace "/mnt/23Q2branch-vol"
                           }
                       }
                 steps {
                     sh "rm -rf *"
                     sh "git clone https://github.com/amitsinha1995/docker.git -b 23Q2branch"
                     sh "chmod 777 *"
                     sh "cp -r index.html server2://usr/local/apache2/htdocs/"
                       }
                                     }

// Cloning 23Q3branch in server3 container synced docker volume-23Q3branch-vol
            stage ('23Q3branch-clone') {
                 agent {
                     label {
                         label 'built-in'
                         customWorkspace "/mnt/23Q3branch-vol"
                           }
                       }
                 steps {
                     sh "rm -rf *"
                     sh "git clone https://github.com/amitsinha1995/docker.git -b 23Q3branch"
                     sh "chmod 777 *"
                     sh "cp -r index.html server3://usr/local/apache2/htdocs/"
                       }
                                    }

// Cloning 23Q4branch in server4 container synced docker volume-23Q4branch-vol
           stage ('23Q4branch-clone') {
                 agent {
                     label {
                         label 'built-in'
                         customWorkspace "/mnt/23Q4branch-vol"
                           }
                       }
                 steps {
                     sh "rm -rf *"
                     sh "git clone https://github.com/amitsinha1995/docker.git -b 23Q4branch"
                     sh "chmod 777 *"
                     sh "cp -r index.html server4://usr/local/apache2/htdocs/"
                       }
                                    }

            
           }
}
