# frame

here you can find all the scripts to have interaction with Frame over API and use Calm to automate Sandbox life cycle from development to final production phase.

Scripts are for demo purposes not for production environment and are not supported by Nutanix in any form.

They assume you have an account on Frame and API keys are generated on Frame control panel.

Scripts are related to automation in managing several sandboxes to update them for example with new software, windows updates, change in configuration,
anything can be done via a powershell script to be run via Calm.

All the scripts require as input API keys and other parameters to interact with the control plane.

there are also 2 scripts used to create/delete endpoint on with Calm and to execute a runbook.

Overall flow is the following:

1. clone a sandbox from a production account to for example a development account, for doing that you need to get Account_IDs from Frame (get_accounts_ID) giving as input name of the account you want to play with
2. poweron the sandbox and get IP address of the sandbox (tested on Nutanix cluster, should work on any other cloud if Calm can reach the sandbox) - sandbox_action
3. use that IP to create an endpoint on Calm (create_endpoint)
4. execute a runbook on that endpoint, here is the change of the sandbox, anything can be passed as powershell script to Calm will work. - execute_runbook
5. delete the endpoint (IP can be variable, so same endpoint could be useless to be kept on Calm)
6. Poweroff sandbox, again script is sandbox_action with passing stop parameter
7. publish sandbox on Frame to be later used for a launchpad and let users assigned to that account to test the change
8. create a launchpad to gain access to latest sandbox

it is possible to move sandbox on various phases from prod -> dev -> test -> final user acceptance test -> production cycling the above automation.
 
