# Create sample use-cases with Postman

When you think about automation, you should start with standardization. Definition of Use-Cases, Naming Convention, and AccessPolicies strategy is a minimum to start with. Once those three points are confirmed, you easily define your automation scripts. For use of our training we will work at three use-cases which very often appears in Customer's designs. 


### Prerequisites - Tenant Common

Configuration in *Common* Tenant is done once at initial config and then reused across EPGs. For that reason, your use-case should contain only Custom Tenant configuration. Configuration of *Common* Tenant can be deployed using already done Postman Requests. Prerequisite, you need to deploy, two VRFs, two Bridge-Domains and EPG_Shared.

Use prepared CSV file for you - [download from here](https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/docs/tenant-common.csv){target=_blank}.

Run same collection which in previous excercise:

<img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/images/tenant-common-coll-1.png" width = 800>

Run ACI dCloud - results should be **200 OK **.


## Use-Case no.1

Customer place network components in ACI shared tenant *common*. Custom tenants contain only EPGs, Domain associations and static-bindings for particular department.

<img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/images/use-case-1.png" width = 800>

Below you can find code for Tenant Custom in use case 1.

		https://{{apic}}/api/node/mo/uni.json


```json title="Tenant Custom Use-Case 1"
{
	"fvTenant": {
		"attributes": {
			"dn": "uni/tn-{{tenantname}}",
			"name": "{{tenantname}}"
		},
		"children": [
			{
				"fvAp": {
					"attributes": {
						"name": "{{ap}}"
					},
					"children": [
						{
							"fvAEPg": {
								"attributes": {
									"name": "{{epgname}}"
								},
								"children": [
									{
										"fvRsDomAtt": {
											"attributes": {
												"tDn": "uni/phys-{{domain}}"
											}
										}
									},
									{
										"fvRsBd": {
											"attributes": {
												"annotation": "",
												"tnFvBDName": "{{bdname}}"
											}
										}
									}
								]
							}
						}
					]
				}
			}
		]
	}
}
```
Run the code with new CSV file which you will use for custom-tenant definition, together with static biding associated to EPGs **[download from here](https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/docs/var-data-uc1.csv){target=_blank}.**

```json title="Tenant Custom Use-Case 1 static biding"
{
	"fvTenant": {
		"attributes": {
			"dn": "uni/tn-{{tenantname}}",
			"name": "{{tenantname}}"
		},
		"children": [
			{
				"fvAp": {
					"attributes": {
						"name": "{{ap}}"
					},
					"children": [
						{
							"fvAEPg": {
								"attributes": {
									"name": "{{epgname}}"
								},
								"children": [
									{
										"fvRsPathAtt": {
											"attributes": {
												"encap": "vlan-{{vlan}}",
												"instrImedcy": "lazy",
												"mode": "{{mode}}",
												"primaryEncap": "unknown",
												"tDn": "topology/pod-{{pod}}/paths-{{leaf}}/pathep-[eth{{interface}}]",
												"userdom": ":all:"
											}
										}
									}
								]
							}
						}
					]
				}
			}
		]
	}
}
```

!!! Tip
	Assumption that Access-Policies, meaning VLAN pool and Domain Association is done beforehand. Otherwise use other Postman Requests to create proper vlan mapping

## Use-Case no.2

Customer place network components in ACI shared tenant *common* as well as Custom Tenant. Moreover custom tenants contain EPGs, Domain associations and static-bindings for particular department.

<img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/images/use-case-2.png" width = 800>

## Use-Case no.3


Customer place SHARED network component in ACI shared tenant *common*. Custom tenants contain dedicated VRF, BDs and EPGs, Domain associations and static-bindings for particular department. L3out configuration for routing with external networks.

<img src="https://raw.githubusercontent.com/marcinduma/ACI-Automation/main/images/use-case-3.png" width = 800>