# jenkins-help

#### Forwarding port 80 traffic to 8080.
sudo iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080  
sudo iptables -t nat -I OUTPUT -p tcp -o lo --dport 80 -j REDIRECT --to-ports 8080  

sudo yum -y install nfs-utils  
mkdir webapp  
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2 fs-a2c40b73.efs.ap-south-1.amazonaws.com:/ webapp  
sudo mount -t nfs4 -o vers=4.1 $(curl -s http://169.254.169.254/latest/metadata/placement/availability-zone).<file-systemid>.efs.<aws-region>.amazonaws.com:/ webapp  
sudo chown -R balaji:balaji webapp  

sudo vi /etc/fstab  
<mount-target-DNS>:/ /mnt/JENKINS_HOME nfs defaults,vers=4.1 0 0  
Refer https://github.com/balajipothula/jenkins-help/blob/master/Jenkins_on_AWS.pdf Page: 19 & 20.  
