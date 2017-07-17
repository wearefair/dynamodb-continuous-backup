PREFIX ?= stage
cfg := "${PREFIX}_config.hjson"
provision := "${PREFIX}_provisioning_whitelist.hjson"

login:
	fair login aws
prep:
	pip install --upgrade boto3 awscli hjson shortuuid

build:
	./build.sh ${cfg}
deploy: login
	./deploy.py --config-file ${cfg}
release: build deploy

# Provision Existing
continuous: login release
	./provision_tables.py ${provision}
deprovision: login
	./deprovision_tables.py ${provision}
