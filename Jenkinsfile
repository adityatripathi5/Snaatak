pipeline {
  agent any

  environment {
    CLAUDE_MODEL = 'claude-3-haiku-20240307'
  }

  stages {
    stage('Pre-flight Dependency Check') {
      steps {
        echo "Checking if PostgreSQL is reachable on port 5432..."
        sh 'nc -z localhost 5432'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean install'
      }
    }
  }

  post {
    failure {
      echo "Build failed. Triggering Claude RCA (non-blocking)..."

      withCredentials([string(credentialsId: 'anthropic-api-key', variable: 'ANTHROPIC_API_KEY')]) {

        script {
          
          def logs = currentBuild.rawBuild.getLog(200).join("\n") 

          sh """
            set +e

            jq -n \
              --arg model "$CLAUDE_MODEL" \
              --arg msg "$logs" \
              '{
                model: \$model,
                max_tokens: 300, 
                messages: [
                  {
                    role: "user",
                    content: ("Jenkins pipeline failed. Analyze the issue and suggest a fix. Logs: " + \$msg)
                  }
                ]
              }' > claude_request.json

            curl --max-time 15 -s https://api.anthropic.com/v1/messages \
              -H "x-api-key: ${ANTHROPIC_API_KEY}" \
              -H "anthropic-version: 2023-06-01" \
              -H "content-type: application/json" \
              -d @claude_request.json \
              -o claude_response.json || true

            jq -r '.content[0].text // "Claude analysis unavailable"' claude_response.json
          """
        }
      }
    }

    success {
      echo "Build successful. Claude analysis not required."
    }
  }
}
