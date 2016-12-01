node('master'){

        try{
                
                stage ('Print'){
                        println "Hello"
			exit 1

                }

	notifyBuild(currentBuild.result,"NULL")
        }
        catch(e)
        {
                notifyBuild("FAILED","${e}")
        }


}


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

step([$class: 'GitHubCommitStatusSetter', statusResultSource: [$class: 'ConditionalStatusResultSource', results: [[$class: 'AnyBuildResult', message: 'done', state: 'SUCCESS']]]])
        echo "status set to ${buildStatus}."


  } else if (buildStatus == 'FAILED') {

    color = 'RED'

    colorCode = '#FF0000'

step([$class: 'GitHubCommitStatusSetter', statusResultSource: [$class: 'ConditionalStatusResultSource', results: [[$class: 'AnyBuildResult', message: 'done', state: 'FAILURE']]]])

        echo "status set to ${buildStatus}."

}
}

