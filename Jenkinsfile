pipeline {
  agent any

  environment {
    CLAUDE_MODEL = 'claude-3-haiku-20240307'
  }

  stages {
    stage('Security Scan') {
      steps {
        script {
          def codeSnippet = """
          const AWS_KEY = 'AKIA1234567890';
          """

          withCredentials([string(credentialsId: 'anthropic-api-key', variable: 'ANTHROPIC_API_KEY')]) {
            sh """
              jq -n \
                --arg model "$CLAUDE_MODEL" \
                --arg msg "$codeSnippet" \
                '{
                  model: \$model,
                  max_tokens: 200,
                  messages: [{
                    role: "user",
                    content: ("Check this code for security risks or secrets. Respond SAFE or explain issue: " + \$msg)
                  }]
                }' > request.json

              curl -s https://api.anthropic.com/v1/messages \
                -H "x-api-key: ${ANTHROPIC_API_KEY}" \
                -H "anthropic-version: 2023-06-01" \
                -H "content-type: application/json" \
                -d @request.json \
                -o response.json || true

              jq -r '.content[0].text // "Security scan unavailable"' response.json
            """
          }
        }
      }
    }
  }
}
