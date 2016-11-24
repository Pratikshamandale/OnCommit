node('master'){

        try{
                stage('Checkout') {

                        checkout scm
                }

                stage ('Print'){
                        println "Hello"
                }

        }
        catch(e)
        {
                notifyBuild("FAILED","${e}")
        }

        notifyBuild(currentBuild.result,"NULL")




def notifyBuild(String buildStatus = 'STARTED',String thiserr) {

  buildStatus =  buildStatus ?: 'SUCCESSFUL'



        def colorName = 'RED'

        def colorCode = '#FF0000'



  if (buildStatus == 'STARTED') {
    color = 'YELLOW'

    colorCode = '#FFFF00'

  } else if (buildStatus == 'SUCCESSFUL') {

    color = 'GREEN'

    colorCode = '#00FF00'

          step([$class: '       ',

        contextSource: [$class: 'ManuallyEnteredCommitContextSource',

        context: 'BUILD STATUS'],

        statusResultSource: [$class: 'ConditionalStatusResultSource',

        results: [[$class: 'AnyBuildResult',

        message: 'SUCCESSFUL',

        state: 'SUCCESS']]]])

        echo "status set to ${buildStatus}."


  } else if (buildStatus == 'FAILED') {

    color = 'RED'

    colorCode = '#FF0000'

          step([$class: 'GitHubCommitStatusSetter',

        contextSource: [$class: 'ManuallyEnteredCommitContextSource',

        context: 'BUILD STATUS'],

        statusResultSource: [$class: 'ConditionalStatusResultSource',

        results: [[$class: 'AnyBuildResult',

        message: 'FAILED',

        state: '${buildStatus}']]]])

        echo "status set to ${buildStatus}."

}
}
}
