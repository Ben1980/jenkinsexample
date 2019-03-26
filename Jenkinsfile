pipeline {
	agent any

	options {
		buildDiscarder(logRotator(numToKeepStr: '10'))
	}

	parameters {
		booleanParam name: 'RUN_TESTS', defaultValue: true, description: 'Run Tests?'
		booleanParam name: 'RUN_ANALYSIS', defaultValue: true, description: 'Run Static Code Analysis?'
		booleanParam name: 'DEPLOY', defaultValue: true, description: 'Deploy Artifacts?'
	}

	stages {
        stage('Build') {
            steps {
                cmake arguments: '-DCMAKE_TOOLCHAIN_FILE=/home/bmahr/Projects/vcpkg/scripts/buildsystems/vcpkg.cmake', installation: 'InSearchPath'
                cmakeBuild buildDir: 'build', buildType: 'Release', cleanBuild: true, installation: 'InSearchPath'
            }
        }

        stage('Test') {
            when {
                environment name: 'GENERATE_TRANSLATIONS', value: 'true'
            }
            steps {
                ctest 'InSearchPath'
            }
        }
//
        //stage('Analyse') {
//
        //}
//
        //stage('Deploy') {
//
        //}
//
//
//
//
//
		//stage('Get from SCM') {
		//	steps {
		//		bat script: "./getFromSCM.bat"
		//	}
		//}
//
		//stage('Generate Translations') {
		//	when {
		//		environment name: 'GENERATE_TRANSLATIONS', value: 'true'
		//	}
		//	steps {
		//		bat script: "./generateTranslation.bat"
		//	}
		//}
//
		//stage('Set Build Number') {
		//	steps {
		//		powershell returnStatus: true, script: "./setBuildNumber.ps1 ${env.BUILD_NUMBER}"
		//	}
		//}
//
		//stage('Cleanup KISSsoft/KISSsys/COM') {
		//	steps {
		//		parallel(
		//			"Cleanup KISSsoft/KISSsys": {
		//				bat script: "\"${tool 'MSBuild2017'}\" KISSsoftKISSsys.sln /t:clean /p:Configuration=Release"
		//			},
		//			"Cleanup COM": {
		//				bat script: "\"${tool 'MSBuild2017'}\" KISSsoftCOM/KISSsoftCOM.sln /t:clean /p:Configuration=Release /p:platform=win32"
		//				bat script: "\"${tool 'MSBuild2017'}\" KISSsoftCOM/KISSsoftCOM.sln /t:clean /p:Configuration=ReleaseCurrentGUID /p:platform=win32"
		//			},
		//			"Cleanup COM-64bit": {
		//				bat script: "\"${tool 'MSBuild2017'}\" KISSsoftCOM/KISSsoftCOM.sln /t:clean /p:Configuration=Release64 /p:platform=x64"
		//				bat script: "\"${tool 'MSBuild2017'}\" KISSsoftCOM/KISSsoftCOM.sln /t:clean /p:Configuration=Release64CurrentGUID /p:platform=x64"
		//			}
		//		)
		//	}
		//}
//
		//stage('Build KISSsoft/KISSsys') {
		//	steps {
		//		//Unfortunately because of bug https://account.qt.io/support/request/INC-1246937 and https://developercommunity.visualstudio.com/content/problem/438167/build-order-not-working-using-msbuild-2.html?childToView=439205#comment-439205
		//		//msbuild can't be used till the issue is resolved. Instead we use devenv as workaround.
		//		//bat script: "\"${tool 'MSBuild2017'}\" KISSsoftKISSsys.sln /p:Configuration=Release /p:PostBuildEventUseInBuild=false"
		//		bat returnStatus: true, script: "./build.bat"
		//	}
		//}
//
		//stage('Build KISSsoftCOM') {
		//	steps {
		//		bat script: "\"${tool 'MSBuild2017'}\" KISSsoftCOM/KISSsoftCOM.sln /p:Configuration=Release /p:platform=win32 /p:PostBuildEventUseInBuild=false"
		//		bat script: "./midl.bat amd64"
		//		bat script: "./midl.bat int64"
//
		//		bat returnStatus: true, script: "\"${tool 'MSBuild2017'}\" KISSsoftCOM/KISSsoftCOM.sln /p:Configuration=Release64 /p:platform=x64 /p:PostBuildEventUseInBuild=false"
		//		bat script: "./midl.bat amd64"
		//		bat script: "\"${tool 'MSBuild2017'}\" KISSsoftCOM/KISSsoftCOM.sln /t:KISSsoftCOMPS /p:Configuration=Release64 /p:platform=x64 /p:PostBuildEventUseInBuild=false /p:BuildProjectReferences=false"
//
		//		bat script: "\"${tool 'MSBuild2017'}\" KISSsoftCOM/KISSsoftCOM.sln /p:Configuration=ReleaseCurrentGUID /p:platform=win32 /p:PostBuildEventUseInBuild=false"
		//		bat script: "./midl.bat amd64"
		//		bat script: "./midl.bat int64"
//
		//		bat returnStatus: true, script: "\"${tool 'MSBuild2017'}\" KISSsoftCOM/KISSsoftCOM.sln /p:Configuration=Release64CurrentGUID /p:platform=x64 /p:PostBuildEventUseInBuild=false"
		//		bat script: "./midl.bat amd64"
		//		bat script: "\"${tool 'MSBuild2017'}\" KISSsoftCOM/KISSsoftCOM.sln /t:KISSsoftCOMPS /p:Configuration=Release64CurrentGUID /p:platform=x64 /p:PostBuildEventUseInBuild=false /p:BuildProjectReferences=false"
		//	}
		//}
//
		//stage('Sign Files') {
		//	steps {
		//		bat script: "./signFiles.bat"
		//	}
		//}
//
		//stage('Generate Installation') {
		//	steps {
		//		powershell returnStatus: true, script: "./copyFiles.ps1 ${env.BUILD_NUMBER} ${env.NUMBER_OF_DAYS}"
		//		bat script: "./produceInstallation.bat"
		//		powershell returnStatus: true, script: "./copyFiles2.ps1 ${env.BUILD_NUMBER} ${env.NUMBER_OF_DAYS}"
		//	}
		//}
//
		//stage('Run Tests') {
		//	when {
		//		environment name: 'RUN_TESTS', value: 'true'
		//	}
		//	options {
		//		timeout(time: 5, unit: 'HOURS')
		//	}
		//	steps {
		//		bat returnStatus: true, script: "./unitTest.bat"
		//		bat returnStatus: true, script: "./unitTestWebApi.bat"
		//		//bat returnStatus: true, script: "./integrationTest.bat"
		//		powershell returnStatus: true, script: "./copyFiles3.ps1"
		//	}
		//}

		//stage('Generate Documentation') {
		//	when {
		//		environment name: 'GENERATE_DOCUMENTATION', value: 'true'
		//	}
		//	steps {
		//		bat returnStatus: true, script: "./generateDocumentation.bat"
		//		bat returnStatus: true, script: "./runCPPCheck.bat"
		//		publishCppcheck allowNoReport: true, ignoreBlankFiles: true, pattern: '**/cppcheck-result.xml'
		//	}
		//}
	}
}
