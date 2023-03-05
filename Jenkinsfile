pipeline {
	  agent {
	    label {
	    	label("built-in")
	    }
      }
	stages{
	stage ("cleaning workspace") {
		steps {
			cleanWs()
		}
	}
	stage ("cheout from Scm") {
		steps {
			checkout scm
		}
	}
 	stage ("install httpd server") {
 		steps {
 		sh 'ansible all -b -m  yum -a "name=httpd state=install" '
 	}
 }	
 	stage ("copy index file") {
 		steps {
         sh 'ansible all -b -m copy -a "src=index.html dest=/var/www/html/ mode=0777"'  
         sh 'ansible all -b -m service -a "name=httpd state=started"' 		
 		}

 	}
 }
}
