pipeline {
  agent any

  environment {
    CLAUDE_MODEL = 'claude-3-haiku-20240307'
  }

  stages {
    stage('Collect Change Context') {
      steps {
        script {
          env.CHANGE_SUMMARY = """
          Service: payment-api
          Changed files:
          - PaymentService.java
          - RetryPolicy.yaml
          Database calls modified
          """
        }
      }
    }

    stage('AI Change Impact Analysis') {
      steps {
        withCredentials([string(credentialsId: 'anthropic-api-key', variable: 'ANTHROPIC_API_KEY')]) {
          sh """
            jq -n \
              --arg model "$CLAUDE_MODEL" \
              --arg msg "$CHANGE_SUMMARY" \
              '{
                model: \$model,
                max_tokens: 300,
                messages: [{
                  role: "user",
                  content: ("Analyze change impact for production systems. Identify affected components, risks, and recommended checks: " + \$msg)
                }]
              }' > request.json

            curl -s https://api.anthropic.com/v1/messages \
              -H "x-api-key: ${ANTHROPIC_API_KEY}" \
              -H "anthropic-version: 2023-06-01" \
              -H "content-type: application/json" \
              -d @request.json \
              -o response.json || true

            jq -r '.content[0].text' response.json
          """
        }
      }
    }
  }
}
