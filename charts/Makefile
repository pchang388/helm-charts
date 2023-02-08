CHART_VERSION=0.1.0
APP_VERSION=v2.7.11
CHART_NAME=simple-unifipoller
DEPLOY_TEST_NAMESPACE=test-unpoller
CHART_FILE=${CHART_NAME}/Chart.yaml
GITHUB_PAGE_REPO=https://pchang388.github.io/helm-charts/


lint:
	helm lint ${CHART_NAME}

dry_run:
	helm install ${DEPLOY_TEST_NAMESPACE} ${CHART_NAME}/ -n ${DEPLOY_TEST_NAMESPACE} --create-namespace --dry-run

# https://github.com/helm/chart-testing
test:
	ct install --chart-dirs . --charts ${CHART_NAME} 

install:
	helm install ${DEPLOY_TEST_NAMESPACE} ${CHART_NAME}/ -n ${DEPLOY_TEST_NAMESPACE} --create-namespace

clean_up:
	helm delete ${DEPLOY_TEST_NAMESPACE} -n ${DEPLOY_TEST_NAMESPACE}
	kubectl delete ns ${DEPLOY_TEST_NAMESPACE}

pkg_helm:
	helm package ${CHART_NAME}

update_index:
	helm repo index ${CHART_NAME}/ --url ${GITHUB_PAGE_REPO}

##  regex: starts with caputres line then replaces
update_versions:
	sed -i 's/^version:.*/version: ${CHART_VERSION}/' ${CHART_FILE}
	sed -i 's/^appVersion:.*/appVersion: ${APP_VERSION}/' ${CHART_FILE}
