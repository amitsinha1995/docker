pipeline {
        agent {
            label {
                label 'built-in' 
                  }
              }
        
        stages {

// I'll create 4 container of httpd image and sync all container with 'docker-volume' where I'll clone my feature branch.
             
             stage ('container-1st-remove') {
                 steps {
                     sh "docker system prune -a -f"
                     sh "rm -rf /mnt/project/*"
                       }
                                                    }

// Cloning 23Q1 branch in server1's synced docker volume-23Q1branch-vol 
           
             stage ('23Q1-branch-clone-and-server1-up') {
                 agent {
                     label {
                         label 'built-in'
                         customWorkspace "/mnt/project/23Q1branch-vol"
                           }
                       }
                 steps {
                     sh "rm -rf *"
                     sh "git clone https://github.com/amitsinha1995/docker-git.git -b 23Q1"
                     sh "chmod 777 docker-git/index.html"
                     sh "docker run -itdp 81:80 -v /mnt/project/23Q1branch-vol/docker-git:/usr/local/apache2/htdocs --name server1 httpd"
                       }
                                         }
            
// Cloning 23Q2 branch in server2's synced docker volume-23Q2branch-vol

             stage ('23Q2-branch-clone-and-server2-up') {
                 agent {
                     label {
                         label 'built-in'
                         customWorkspace "/mnt/project/23Q2branch-vol"
                           }
                       }
                 steps {
                     sh "rm -rf *"
                     sh "git clone https://github.com/amitsinha1995/docker-git.git -b 23Q2"
                     sh "chmod 777 docker-git/index.html"
                     sh "docker run -itdp 82:80 -v /mnt/project/23Q2branch-vol/docker-git:/usr/local/apache2/htdocs --name server2 httpd"
                       }
                                     }

// Cloning 23Q3 branch in server3's synced docker volume-23Q3branch-vol

            stage ('23Q3-branch-clone-and-server3-up') {
                 agent {
                     label {
                         label 'built-in'
                         customWorkspace "/mnt/project/23Q3branch-vol"
                           }
                       }
                 steps {
                     sh "rm -rf *"
                     sh "git clone https://github.com/amitsinha1995/docker-git.git -b 23Q3"
                     sh "chmod 777 docker-git/index.html"
                     sh "docker run -itdp 83:80 -v /mnt/project/23Q3branch-vol/docker-git:/usr/local/apache2/htdocs --name server3 httpd"
                       }
                                       }

// Cloning 23Q4 branch in server4's synced docker volume-23Q4branch-vol

           stage ('23Q4-branch-clone-and-server4-up') {
                 agent {
                     label {
                         label 'built-in'
                         customWorkspace "/mnt/project/23Q4branch-vol"
                           }
                       }
                 steps {
                     sh "rm -rf *"
                     sh "git clone https://github.com/amitsinha1995/docker-git.git -b 23Q4"
                     sh "chmod 777 docker-git/index.html"
                     sh "docker run -itdp 84:80 -v /mnt/project/23Q4branch-vol/docker-git:/usr/local/apache2/htdocs --name server4 httpd"
                       }
                                      }

            
           }
}
