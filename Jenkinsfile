pipeline {
  agent any

  environment {
    CLAUDE_MODEL = 'claude-3-haiku-20240307'
  }

  stages {
    stage('Deployment Risk Check') {
      steps {
        script {
          def changeSummary = """
          Updated database connection logic
          Modified authentication flow
          """

          withCredentials([string(credentialsId: 'anthropic-api-key', variable: 'ANTHROPIC_API_KEY')]) {
            sh """
              jq -n \
                --arg model "$CLAUDE_MODEL" \
                --arg msg "$changeSummary" \
                '{
                  model: \$model,
                  max_tokens: 200,
                  messages: [{
                    role: "user",
                    content: ("Assess deployment risk as LOW/MEDIUM/HIGH and explain: " + \$msg)
                  }]
                }' > request.json

              curl -s https://api.anthropic.com/v1/messages \
                -H "x-api-key: ${ANTHROPIC_API_KEY}" \
                -H "anthropic-version: 2023-06-01" \
                -H "content-type: application/json" \
                -d @request.json \
                -o response.json || true

              jq -r '.content[0].text // "Risk assessment unavailable"' response.json
            """
          }
        }
      }
    }
  }
}
