/*
pipeline {
//   agent any
  agent {
    // Run on a build agent where we have the Android SDK installed
    label 'android'
  }
  stages {
    stage('Compile') {
      steps {
        // Compile the app and its dependencies
        sh './gradlew compileDebugSources'
      }
    }
    stage('Unit test') {
      steps {
        // Compile and run the unit tests for the app and its dependencies
        sh './gradlew testDebugUnitTest'

        // Analyse the test results and update the build result as appropriate
        junit '**//*
TEST-*.xml'
      }
    }
    stage('Build APK') {
      steps {
        // Finish building and packaging the APK
        sh 'gradlew assembleDebug'

        // Archive the APKs so that they can be downloaded from Jenkins
        archiveArtifacts '** /*
*/
/*.apk'
      }
    }
//     stage('Static analysis') {
//       steps {
//         // Run Lint and analyse the results
//         sh './gradlew lintDebug'
//         androidLintParser pattern: '**//*
lint-results-*.xml'
//       }
//       post {
//         success {
//           // Notify if the upload succeeded
//           mail to: 'cuongpm5295@gmail.com', subject: 'New build available!', body: 'Check it out!'
//         }
//       }
//     }
//     stage('Deploy') {
//       when {
//         // Only execute this stage when building from the `beta` branch
//         branch 'beta'
//       }
//       environment {
//         // Assuming a file credential has been added to Jenkins, with the ID 'my-app-signing-keystore',
//         // this will export an environment variable during the build, pointing to the absolute path of
//         // the stored Android keystore file.  When the build ends, the temporarily file will be removed.
//         SIGNING_KEYSTORE = credentials('my-app-signing-keystore')
//
//         // Similarly, the value of this variable will be a password stored by the Credentials Plugin
//         SIGNING_KEY_PASSWORD = credentials('my-app-signing-password')
//       }
//       steps {
//         // Build the app in release mode, and sign the APK using the environment variables
//         sh './gradlew assembleRelease'
//
//         // Archive the APKs so that they can be downloaded from Jenkins
//         archiveArtifacts '** /*
*/
/*.apk'
//
//         // Upload the APK to Google Play
//         androidApkUpload googleCredentialsId: 'Google Play', apkFilesPattern: '** /*
*/
/*-release.apk', trackName: 'beta'
//       }
//       post {
//         success {
//           // Notify if the upload succeeded
//           mail to: 'cuongpm5295@gmail.com', subject: 'New build available!', body: 'Check it out!'
//         }
//       }
//     }
  }
  post {
    failure {
      // Notify developer team of the failure
      mail to: 'cuongpm5295@gmail.com', subject: 'Oops!', body: "Build ${env.BUILD_NUMBER} failed; ${env.BUILD_URL}"
    }
  }
} */

pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                android {
                    sdkPackage "build-tools;29.0.2"
                    sdkPackage "platforms;android-29"

                    target 'testDebug'
                }
            }
        }
    }
}
