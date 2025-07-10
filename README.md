
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

---

## ⚙️ Key Steps

### ✅ 1. Create Azure Resource Group
```bash
az group create --name AzureArcLab --location westus2
![Image Alt](https://github.com/Talk2Babatunde/azure-arc-onboarding/blob/333fd74c4814ad3e69bc909bac81d8ce1b094b46/Resource-group-created.png.png).

### ✅ 2. Create Service Principal
```bash
az ad sp create-for-rbac --name "AzureArcSP" \
  --role "Contributor" \
  --scopes /subscriptions/<sub-id>/resourceGroups/AzureArcLab \
  --sdk-auth > azurearc-sp.json
```

### ✅ 3. Install Agent on Ubuntu VM
```bash
wget https://aka.ms/azcmagent -O install_linux_azcmagent.sh
chmod +x install_linux_azcmagent.sh
sudo ./install_linux_azcmagent.sh
```

### ✅ 4. Connect Ubuntu to Azure Arc
```bash
sudo azcmagent connect \
  --resource-group "AzureArcLab" \
  --tenant-id "<tenantId>" \
  --subscription-id "<subId>" \
  --location "westus2" \
  --cloud "AzureCloud" \
  --service-principal-id "<clientId>" \
  --service-principal-secret "<clientSecret>" \
  --tags 'Project=AzureArcLab,Owner=Babatunde,UseCase=SOC-Lab,OS=Ubuntu'
```

---

## ✅ Results

- Machine appears under **Azure Arc → Servers**
- Name: `babatunde-VirtualBox`
- Tags applied: `Owner`, `UseCase`, `Project`, etc.
- Status: ✅ Connected
- Resource Group: `AzureArcLab`

![Azure Portal Screenshot](screenshots/azure-arc-connected.png)

---

## 📸 Screenshots

Include:
- ✅ Terminal output of `azcmagent connect`
- ✅ Azure Portal → Azure Arc → Servers
- ✅ Tag and Resource Group views

Place your images in a `/screenshots` folder and use relative links like `![Alt](screenshots/yourimage.png)`

---

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
