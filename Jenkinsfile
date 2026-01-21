pipeline {
  agent any

  environment {
    CLAUDE_MODEL = 'claude-3-haiku-20240307'
  }

  stages {
    stage('Build') {
      steps {
        echo "Simulating build..."
        sh 'echo Build completed'
      }
    }
  }

  post {
    always {
      echo "Generating AI log summary..."

      withCredentials([string(credentialsId: 'anthropic-api-key', variable: 'ANTHROPIC_API_KEY')]) {
        script {
          def logs = currentBuild.rawBuild.getLog(200).join("\n")

          sh """
            jq -n \
              --arg model "$CLAUDE_MODEL" \
              --arg msg "$logs" \
              '{
                model: \$model,
                max_tokens: 200,
                messages: [{
                  role: "user",
                  content: ("Summarize this Jenkins pipeline execution in plain English: " + \$msg)
                }]
              }' > request.json

            curl -s https://api.anthropic.com/v1/messages \
              -H "x-api-key: ${ANTHROPIC_API_KEY}" \
              -H "anthropic-version: 2023-06-01" \
              -H "content-type: application/json" \
              -d @request.json \
              -o response.json || true

            jq -r '.content[0].text // "Summary unavailable"' response.json
          """
        }
      }
    }
  }
}
