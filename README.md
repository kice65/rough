How to install Maven in Amazon Linux 

==================================================CONNECTING YOUR EC2 TO YOUR VIRTUAL MACHINE===============================================
Open your virtual machine and SSH into your EC2 server
Step 1: Connect to Your EC2 Server Using MobaXterm

Open MobaXterm

Click Session → SSH

Enter:

Remote host: your-ec2-public-ip

Username:

ec2-user (Amazon Linux)

Use your .pem key under Advanced SSH settings

Once connected, you’ll see something like:
[ec2-user@ip-172-31-x-x ~]$
✅ Step 2: Update Your Server

Run:
sudo yum update -y
If you're on Amazon Linux 2023:
sudo dnf update -y

✅ Step 3: Install Java (Required for Maven)

Maven requires Java.

Install OpenJDK 17 (recommended):
sudo yum install java-17-openjdk -y

Verify:
Step 4: Install Maven
🔹 Option 1 (Easiest – Using Package Manager)
Amazon Linux 2:
sudo yum install maven -y
Amazon Linux 2023:
sudo dnf install maven -y

Verify installation:

mvn -version

You should see something like:

Apache Maven 3.x.x
Java version: 17
🔹 Option 2 (Manual Installation – Recommended for DevOps Learning)

If you want full DevOps control (good for interviews), install manually:

1️⃣ Download Maven

Go to Apache Maven official site and copy the latest version link.

Example:

cd /opt
sudo wget https://downloads.apache.org/maven/maven-3/3.9.6/binaries/apache-maven-3.9.6-bin.tar.gz
2️⃣ Extract
sudo tar -xvzf apache-maven-3.9.6-bin.tar.gz

Rename:

sudo mv apache-maven-3.9.6 maven
3️⃣ Set Environment Variables

Edit profile:

sudo nano /etc/profile.d/maven.sh

Add:

export M2_HOME=/opt/maven
export PATH=$M2_HOME/bin:$PATH

Save and exit.

Make it executable:

sudo chmod +x /etc/profile.d/maven.sh

Load it:

source /etc/profile.d/maven.sh
4️⃣ Verify
mvn -version

java -version
