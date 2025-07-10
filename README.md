
# 🔗 Azure Arc Onboarding Project

This project demonstrates how I successfully onboarded a **Ubuntu 22.04 LTS virtual machine** to **Azure Arc** using a **Service Principal** for secure, non-interactive authentication. The project simulates a real-world hybrid environment, where on-premises resources are managed from Azure.

---

## 📌 Objectives

- Connect a non-Azure Ubuntu server to Azure Arc
- Use service principal authentication (non-interactive)
- Apply tagging and metadata for classification
- Prepare for hybrid governance and automation use cases

---

## 🛠️ Tools & Technologies

- Azure CLI
- Azure Portal
- Ubuntu 22.04 LTS (VirtualBox)
- Azure Arc Connected Machine Agent (`azcmagent`)
- Azure Active Directory (Service Principal)
- RBAC (Role-Based Access Control)




## ⚙️ Key Steps

### ✅ 1. Create Azure Resource Group
bash
az group create --name AzureArcLab --location westus2
![Alt]: <https://github.com/Talk2Babatunde/azure-arc-onboarding/blob/main/Resource-group-created.png.png?raw=true>


### ✅ 2. Create Service Principal
bash
az ad sp create-for-rbac --name "AzureArcSP" \
  --role "Contributor" \
  --scopes /subscriptions/<sub-id>/resourceGroups/AzureArcLab \
  --sdk-auth > azurearc-sp.json
![Alt]: <https://github.com/Talk2Babatunde/azure-arc-onboarding/blob/main/create-a-Service-Principal-named-AzureArcSP-07-09-2025_06_35_PM.png?raw=true>

### ✅ 3. Install Agent on Ubuntu VM
bash
wget https://aka.ms/azcmagent -O install_linux_azcmagent.sh
chmod +x install_linux_azcmagent.sh
sudo ./install_linux_azcmagent.sh
![Alt]: <https://github.com/Talk2Babatunde/azure-arc-onboarding/blob/main/Azure%20Arc%20Agent%20Installation%20on%20Ubuntu%20Terminal.png?raw=true>

### ✅ 4. Connect Ubuntu to Azure Arc
bash
sudo azcmagent connect \
  --resource-group "AzureArcLab" \
  --tenant-id "<tenantId>" \
  --subscription-id "<subId>" \
  --location "westus2" \
  --cloud "AzureCloud" \
  --service-principal-id "<clientId>" \
  --service-principal-secret "<clientSecret>" \
  --tags 'Project=AzureArcLab,Owner=Babatunde,UseCase=SOC-Lab,OS=Ubuntu'
![Alt]: <https://github.com/Talk2Babatunde/azure-arc-onboarding/blob/main/onboarding%20Arc%20to%20Ubuntu.png?raw=true>

---

## ✅ Results

- Machine appears under **Azure Arc → Servers**
- Name: `babatunde-VirtualBox`
- Tags applied: `Owner`, `UseCase`, `Project`, etc.
- Status: ✅ Connected
- Resource Group: `AzureArcLab`

![Azure Portal Screenshot] <https://github.com/Talk2Babatunde/azure-arc-onboarding/blob/main/azure-arc-connected-machine-overview.png?raw=true>

Include:

---

Include:
- ✅ Terminal output of `azcmagent connect`
- ✅ Azure Portal → Azure Arc → Servers
- ✅ Tag and Resource Group views


## 💡 Key Takeaways

- Service Principal onboarding is ideal for automation and scripting
- Azure Arc enables governance, policy, and security over non-Azure machines
- Real-world hybrid scenarios can be simulated from VirtualBox or Docker

---

## 👨‍💼 About Me

**Babatunde Qodri**  
Cloud security administrator  
🔗 [LinkedIn](www.linkedin.com/in/babatunde-qodri-27716b1a5)  
📫 [Email](babatundeliatan@gmail.com)
