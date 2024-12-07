pipeline{
// need to add agents
agent any
tools{
// here mymaven is tool configured under global tool configuration
// new tools added
maven 'mymaven'
}
stages{
{
stage('Clone repo')
steps{
}
git 'https://github.com/github-simplilearn-net/MavenBuild.git'
}
stage('Compile Code')
{
steps{
sh 'mvn compile'
}
}
stage('Test Code')
{
steps{
sh 'mvn test'
}
post{
success{
junit 'target/surefire-reports/*.xml'
}
}
}
stage('Package Code')
{
steps{
sh 'mvn package'
}
}
}
}
