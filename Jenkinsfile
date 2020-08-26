pipeline {
    agent any

    stage ('Static code analysis') {
    sh "sudo phpcs --config-set ignore_warnings_on_exit 1 --report=checkstyle --report-file=checkstyle-result.xml -q /code"
    step([$class: 'hudson.plugins.checkstyle.CheckStylePublisher', pattern: 'checkstyle-*'])
}