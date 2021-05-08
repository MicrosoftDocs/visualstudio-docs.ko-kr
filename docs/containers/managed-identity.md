---
title: Bridge to Kubernetes로 관리 ID를 사용하는 방법
ms.technology: vs-azure
ms.date: 04/28/2021
ms.topic: conceptual
description: Bridge to Kubernetes로 AKS 클러스터에서 Azure AD(Azure Active Directory) 관리 ID를 사용하는 방법을 알아봅니다.
monikerRange: '>=vs-2019'
manager: jmartens
author: ghogen
ms.author: ghogen
ms.openlocfilehash: e4847b25531b48c8200a2620ca3e975f9677c881
ms.sourcegitcommit: 60b7a6159045a44293043a519c8ea6d915bf2c31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2021
ms.locfileid: "108335104"
---
# <a name="use-managed-identity-with-bridge-to-kubernetes"></a>Bridge to Kubernetes로 관리 ID 사용

AKS 클러스터에서 [관리 ID](/azure/active-directory/managed-identities-azure-resources/overview) 보안 기능을 사용하여 비밀 및 리소스에 대한 액세스를 보호하는 경우 Bridge to Kubernetes가 이 기능과 작동할 수 있도록 하려면 특별한 구성이 필요합니다. 로컬 실행과 디버깅이 적절히 보호되도록 하려면 Azure AD(Active Directory) 토큰을 로컬 머신에 다운로드해야 하며 이렇게 하려면 Bridge to Kubernetes에 특별한 구성이 필요합니다. 이 문서에서는 관리 ID를 사용하는 서비스와 작동하도록 Bridge to Kubernetes를 구성하는 방법을 보여 줍니다.

## <a name="how-to-configure-your-service-to-use-managed-identity"></a>관리 ID를 사용하도록 서비스를 구성하는 방법

관리 ID를 지원하는 로컬 머신를 사용하도록 설정하려면 *KubernetesLocalConfig.yaml* 파일의 `enableFeatures` 섹션에서 `ManagedIdentity`를 추가합니다. `enableFeatures` 섹션이 아직 없으면 추가합니다.

```yaml
enableFeatures:
    ManagedIdentity
```

> [!WARNING]
> Azure AD 토큰이 로컬 머신으로 페치되어 보안 위험을 발생시킬 수 있으므로 프로덕션 클러스터가 아닌 개발 클러스터로 작업하는 경우에만 Bridge to Kubernetes에 관리 ID를 사용해야 합니다.

*KubernetesLocalConfig.yaml* 파일이 없으면 만들 수 있습니다. [방법: Bridge to Kubernetes 구성](configure-bridge-to-kubernetes.md)을 참조하세요.

## <a name="how-to-fetch-the-azure-active-directory-tokens"></a>Azure Active Directory 토큰을 페치하는 방법

토큰을 페치할 때 코드에서 <xref:Azure.Identity.DefaultAzureCredential> 또는 <xref:Azure.Identity.ManagedIdentityCredential>을 사용하고 있는지 확인해야 합니다.

다음 C# 코드는 `ManagedIdentityCredential`을 사용할 때 스토리지 계정 자격 증명을 페치하는 방법을 보여 줍니다.

```csharp
var credential = new ManagedIdentityCredential(miClientId);
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

다음 코드는 DefaultAzureCredential을 사용할 때 스토리지 계정 자격 증명을 페치하는 방법을 보여 줍니다.

```csharp
var credential = new DefaultAzureCredential();
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

관리 ID를 사용하여 다른 Azure 리소스에 액세스하는 방법을 알아보려면 [다음 단계](#next-steps) 섹션을 참조하세요.

## <a name="receive-azure-alerts-when-tokens-are-downloaded"></a>토큰이 다운로드될 때 Azure 경고 수신

서비스에서 Bridge to Kubernetes를 사용할 때마다 Azure AD 토큰이 로컬 머신에 다운로드됩니다. Azure 경고를 사용하도록 설정하여 Azure AD 토큰이 로컬 머신에 다운로드될 때 알림을 받을 수 있습니다. 자세한 내용은 [Azure Defender 사용](/azure/security-center/enable-azure-defender)을 참조하세요. 30일 체험 기간이 끝난 후에는 요금이 청구됩니다.

## <a name="next-steps"></a>다음 단계

관리 ID를 사용하는 AKS 클러스터에서 작동하도록 Bridge to Kubernetes를 구성했으므로 이제 평소대로 디버그할 수 있습니다. [bridge-to-kubernetes.md#connect-to-your-cluster-and-debug-a-service]를 참조하세요.

다음 자습서에 따라 관리 ID를 사용하여 Azure 리소스에 액세스하는 방법에 대해 자세히 알아보세요.

- [자습서: Linux VM 시스템 할당 관리 ID를 사용하여 Azure Storage에 액세스](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-storage)
- [자습서: Linux VM 시스템 할당 관리 ID를 사용하여 Azure Data Lake Store에 액세스](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-datalake)
- [자습서: Linux VM 시스템 할당 관리 ID를 사용하여 Azure Key Vault에 액세스](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-nonaad)

관리 ID를 사용하여 다른 Azure 리소스에 액세스하는 방법에 대한 다른 자습서도 해당 섹션에 있습니다.

## <a name="see-also"></a>참고 항목

[Azure Active Directory](/azure/active-directory/managed-identities-azure-resources/)
