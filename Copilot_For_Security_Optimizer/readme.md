# CopilotforSecurity-Scaler
Author: Lachlan Watson

This solution will allow you to view and control the Copilot for Security Compute Capacity.<br>
The solution is created using 2 components:
- Sentinel Workbook - Copilot for Security Optimizer
- Playbook (Logic App) - Copilot for Security Scaler

![Solution Architecture](./images/Copilot_For-Security_Optimizer_solution-architecture.png)

The Copilot for Security Optimizer Sentinel solution has 3 distinct features. <br>It is used to view and deploy a schedule to a Copilot for Security Compute Capacity by applying and interpreting Azure Resource Tags.  In the event of a SOC operating in a more limited capacity than 24x7 such as 8x5 this can mean significant cost savings by allowing the playbook to scale the compute capacity according to the schedule that has been applied.<br>

[Learn more about Copilot for Security](https://learn.microsoft.com/en-us/copilot/security/microsoft-security-copilot)<br>
[Learn more about Playbooks (Logic Apps)](https://learn.microsoft.com/en-us/azure/logic-apps/logic-apps-overview)<br>
[Learn more about Workbooks](https://learn.microsoft.com/en-us/azure/azure-monitor/visualize/workbooks-overview)<br>

## Prerequisites
Ideally you already have a Copilot for Security Compute Capacity deployed, if not you should considering deploying a compute capacity in the near future, as all capabilities of this solution rely on having a compute capacity already deployed.

Least-privilege resource deployment requires:
- Workbook - Monitoring Contributor
- Playbook - Logic App Contributor

Post-config requirements:
Subscription Owner is required to create and apply a least-privilege custom role for the Playbook. You may choose to assign the Contributor role if you do not want to use a custom role.<br>

## Deployment
**Deploy Solution**

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FLSLWatson%2FCopilotForSecurity%2Fmain%2FCopilot_For_Security_Optimizer%2Fsolution%2Fazuredeploy.json)


## Post-deployment
1. (Optional) Deploy the Copilot for Security Capacity Creator role to each subscription where Copilot for Security Compute Capacities are present for a least-privilege approach<br>
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FLSLWatson%2FCopilotForSecurity%2Fmain%2FCopilot_For_Security_Optimizer%2Fcustomrole%2Fazuredeploy.json)

2. Assign the Copilot for Security Capacity Creator custom role, or Contributor built-in role to the Playbook's managed identity - https://docs.microsoft.com/azure/logic-apps/create-managed-service-identity?tabs=consumption#assign-managed-identity-role-based-access-in-the-azure-portal

3. Open the playbook in the Logic App Designer and ensure connections are displaying correctly<br><br>

## Screenshots
**Workbook - View No Schedule**<br>
![Workbook View - Dark](./images/Copilot_For_Security_Optimizer_View_Black.png)
![Workbook View - Light](./images/Copilot_For_Security_Optimizer_View_White.png)<br><br>
**Workbook - Apply/Modify Schedule**<br>
![Workbook Edit - Dark](./images/Copilot_For_Security_Optimizer_Edit_Black.png)
![Workbook Edit - Light](./images/Copilot_For_Security_Optimizer_Edit_White.png)<br><br>
**Playbook**<br>
![Playbook Overview - Dark](./images/Copilot_For_Security_Optimizer_Scaler_Logicapp_Dark.png)
![Playbook Ovewview - Light](./images/Copilot_For_Security_Optimizer_Scaler_Logicapp_White.png)