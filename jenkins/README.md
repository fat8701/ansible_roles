# Ansible Role: Jenkins 

安装Jenkins 

## 介绍
Jenkins 是一个开源项目，提供了一种易于使用的持续集成系统，使开发者从繁杂的集成中解脱出来，专注于更为重要的业务逻辑实现上。同时 Jenkins 能实施监控集成中存在的错误，提供详细的日志文件和提醒功能，还能用图表的形式形象地展示项目构建的趋势和稳定性。

官方： https://jenkins.io/
github: https://github.com/jenkinsci/jenkins

## 要求

此角色仅在RHEL及其衍生产品上运行。

## 测试环境

ansible `2.3.2.0`
os `Centos 7.2 X64`

## 角色变量
	software_files_path: "/opt/software"
	
	jenkins_repo_url: https://pkg.jenkins.io/redhat/jenkins.repo
	jenkins_repo_key_url: https://pkg.jenkins.io/redhat/jenkins.io.key
	jenkins_pkg_url: https://pkg.jenkins.io/redhat-stable
	
	jenkins_version: "2.60.3"
	
	jenkins_home: /home/jenkins
	jenkins_hostname: localhost
	jenkins_http_port: 9999
	jenkins_jar_location: "{{ software_files_path }}/jenkins-cli.jar"
	jenkins_url_prefix: ""
	jenkins_java_options: "-Djenkins.install.runSetupWizard=false"
	
	jenkins_admin_username: admin
	jenkins_admin_password: admin
	
	jenkins_init_file: /etc/sysconfig/jenkins
	jenkins_init_changes:
	  - option: "JENKINS_ARGS"
	    value: "--prefix={{ jenkins_url_prefix }}"
	  - option: "JENKINS_JAVA_OPTIONS"
	    value: "{{ jenkins_java_options }}"
	    
	jenkins_plugins_recommended:    
	  - antisamy-markup-formatter         
	  - bouncycastle-api                  
	  - structs                           
	  - ant                               
	  - credentials                       
	  - pam-auth                          
	  - ssh-credentials                   
	  - ansible                           
	  - msbuild                           
	  - gradle                            
	  - javadoc                           
	  - junit                             
	  - windows-slaves                    
	  - display-url-api                   
	  - mailer                            
	  - maven-plugin                      
	  - ldap                              
	  - workflow-step-api                 
	  - scm-api                           
	  - workflow-api                      
	  - pipeline-model-definition         
	  - pipeline-milestone-step           
	  - external-monitor-job              
	  - jquery-detached                   
	  - ace-editor                        
	  - timestamper                       
	  - workflow-scm-step                 
	  - resource-disposer                 
	  - script-security                   
	  - ws-cleanup                        
	  - workflow-support                  
	  - workflow-cps                      
	  - pipeline-input-step               
	  - pipeline-stage-step               
	  - workflow-job                      
	  - workflow-aggregator               
	  - pipeline-graph-analysis           
	  - pipeline-rest-api                 
	  - handlebars                        
	  - momentjs                          
	  - pipeline-stage-view               
	  - pipeline-build-step               
	  - plain-credentials                 
	  - credentials-binding               
	  - pipeline-model-api                
	  - token-macro                       
	  - pipeline-model-extensions         
	  - git-client                        
	  - cloudbees-folder                  
	  - git-server                        
	  - config-file-provider              
	  - workflow-cps-global-lib           
	  - branch-api                        
	  - workflow-multibranch              
	  - icon-shim                         
	  - authentication-tokens             
	  - docker-commons                    
	  - durable-task                      
	  - publish-over-ssh                  
	  - workflow-durable-task-step        
	  - docker-workflow                   
	  - nodejs                            
	  - pipeline-stage-tags-metadata      
	  - workflow-basic-steps              
	  - pipeline-model-declarative-agent  
	  - matrix-auth                       
	  - matrix-project                    
	  - build-timeout                     
	  - email-ext                         
	  - git                               
	  - mapdb-api                         
	  - subversion                        
	  - ssh-slaves                        
	  - jquery                            
	  - extended-choice-parameter         
	  - sse-gateway                       
	  - ansicolor                         
	  - blueocean-events                  
	  - extensible-choice-parameter       
	  - dashboard-view                    
	  - role-strategy                     
	  - jackson2-api                      
	  - github-api                        
	  - github                            
	  - blueocean-dashboard               
	  - github-branch-source              
	  - blueocean-commons                 
	  - blueocean                         
	  - blueocean-rest                    
	  - kubernetes                        
	  - pubsub-light                      
	  - blueocean-pipeline-scm-api        
	  - htmlpublisher                     
	  - run-condition                     
	  - variant                           
	  - next-executions                   
	  - metrics                           
	  - blueocean-web                     
	  - blueocean-jwt                     
	  - favorite                          
	  - jira                              
	  - blueocean-rest-impl               
	  - blueocean-pipeline-editor         
	  - blueocean-pipeline-api-impl       
	  - blueocean-github-pipeline         
	  - blueocean-i18n                    
	  - blueocean-git-pipeline            
	  - favorite-view                     
	  - blueocean-config                  
	  - mercurial                         
	  - cloudbees-bitbucket-branch-source 
	  - blueocean-bitbucket-pipeline      
	  - blueocean-personalization         
	  - blueocean-display-url             
	  - blueocean-autofavorite            
	  - create-fingerprint                
	  - pipeline-github-lib               
	  - github-organization-folder        
	  - run-condition-extras              
	  - conditional-buildstep             
	  - parameterized-trigger             
	  - build-pipeline-plugin             
	  - build-timestamp                   
	  - mask-passwords
	  - zentimestamp
	  - email-ext-recipients-column
	  - emailext-template
	  - play-autotest-plugin
	
	jenkins_plugins_extra: []
	
	ansible_python_interpreter: /usr/bin/python2.7



## 依赖
Java (2.53以上版本需要1.8+)


## Example Playbook
	- hosts: node1
	  roles:
		- jenkins
		
	- hosts: node1
	  vars：
	   - jenkins_version: 2.60.3
	   - jenkins_http_port： 9999
	   - jenkins_plugins_extra：
	       - display-console-output
	       - ansible
	  roles:
		- jenkins
		
## 使用
service jenkins
Usage: /etc/init.d/jenkins {start|stop|status|try-restart|restart|force-reload|reload|probe}
