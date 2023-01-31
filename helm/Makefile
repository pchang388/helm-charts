CHART_NAME=simple-unifipoller
DEPLOY_TEST_NAMESPACE=test-unpoller
# CHART_DIR=helm/${CHART_NAME}

lint:
	helm lint ${CHART_NAME}

# https://github.com/helm/chart-testing
test:
	ct install --chart-dirs . --charts ${CHART_NAME} 

dry_run:
	helm install ${DEPLOY_TEST_NAMESPACE} ${CHART_NAME}/ -n ${DEPLOY_TEST_NAMESPACE} --create-namespace --dry-run

install:
	helm install ${DEPLOY_TEST_NAMESPACE} ${CHART_NAME}/ -n ${DEPLOY_TEST_NAMESPACE} --create-namespace