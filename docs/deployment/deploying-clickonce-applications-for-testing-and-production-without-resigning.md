---
title: 다시 서명하지 않고 ClickOnce 앱 배포
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89e1d7970b26d5ba9bd49090362a6a4e8c09f78d
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395329"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>삭제하지 않고 테스트 및 프로덕션 서버를 위한 ClickOnce 응용 프로그램 배포
이 문서에서는 .NET Framework 버전 3.5에 도입된 ClickOnce의 기능에 대해 설명하며, 이 기능을 통해 ClickOnce 매니페스트에 다시 서명하거나 변경하지 않고도 여러 네트워크 위치에서 ClickOnce 응용 프로그램을 배포할 수 있습니다.

> [!NOTE]
> 사임은 여전히 새 버전의 응용 프로그램을 배포하는 데 선호되는 방법입니다. 가능하면 사임 방법을 사용하십시오. 자세한 내용은 [ *Mage.exe(매니페스트* 생성 및 편집 도구)를](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)참조하십시오.

 타사 개발자와 ISV는 이 기능을 선택할 수 있으므로 고객이 응용 프로그램을 보다 쉽게 업데이트할 수 있습니다. 이 기능은 다음과 같은 상황에서 사용할 수 있습니다.

- 응용 프로그램을 업데이트할 때는 응용 프로그램의 첫 번째 설치가 아닙니다.

- 컴퓨터에 응용 프로그램의 구성이 하나만 있는 경우 예를 들어 응용 프로그램이 서로 다른 두 데이터베이스를 가리키도록 구성된 경우 이 기능을 사용할 수 없습니다.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>배포 제안에서 배포 매니페스트에서 제외
 .NET Framework 2.0 및 .NET Framework 3.0에서는 오프라인 가용성을 위해 시스템에 설치되는 모든 `deploymentProvider` ClickOnce 응용 프로그램은 배포 매니페스트에 a를 나열해야 합니다. 는 `deploymentProvider` 업데이트 위치라고도 합니다. ClickOnce가 응용 프로그램 업데이트를 확인하는 위치입니다. 이 요구 사항과 함께 응용 프로그램 게시자가 배포에 서명해야 하므로 회사에서 공급업체 또는 다른 타사에서 ClickOnce 응용 프로그램을 업데이트하기가 어려웠습니다. 또한 동일한 네트워크의 여러 위치에서 동일한 응용 프로그램을 배포하기가 더 어려워집니다.

 .NET Framework 3.5에서 ClickOnce를 변경한 경우 타사에서 ClickOnce 응용 프로그램을 다른 조직에 제공할 수 있으며, 이 응용 프로그램은 자체 네트워크에 배포할 수 있습니다.

 이 기능을 활용하려면 ClickOnce 응용 프로그램의 개발자는 배포 `deploymentProvider` 매니페스트에서 제외해야 합니다. 이 요구 사항은 Mage.exe를 `-providerUrl` 사용하여 배포 매니페스트를 만들 때 인수를 제외해야 함을 의미합니다. 또는 MageUI.exe를 사용 하 여 배포 매니페스트를 생성 하는 경우 응용 **프로그램 매니페스트** 탭에 **시작 위치** 텍스트 상자가 비어 있는지 확인 해야 합니다.

## <a name="deploymentprovider-and-application-updates"></a>배포공급자 및 응용 프로그램 업데이트
 .NET Framework 3.5부터 온라인 및 오프라인 사용 `deploymentProvider` 모두에 대해 ClickOnce 응용 프로그램을 배포하기 위해 배포 매니페스트에 더 이상 지정할 필요가 없습니다. 이 변경은 배포를 직접 패키징하고 서명해야 하지만 다른 회사에서 네트워크를 통해 응용 프로그램을 배포할 수 있는 시나리오를 지원합니다.

 기억해야 할 중요한 점은 a를 `deploymentProvider` 제외하는 응용 프로그램은 태그가 포함된 업데이트를 다시 `deploymentProvider` 제공할 때까지 업데이트 중에 설치 위치를 변경할 수 없다는 것입니다.

 다음은 이 점을 명확히 하는 두 가지 예입니다. 첫 번째 예에서는 태그가 없는 `deploymentProvider` ClickOnce 응용 프로그램을 게시하고 에서 `http://www.adatum.com/MyApplication/`설치하도록 사용자에게 요청합니다. 에서 응용 프로그램의 다음 업데이트를 게시하려는 경우 `http://subdomain.adatum.com/MyApplication/` `http://www.adatum.com/MyApplication/`에 있는 배포 매니페스트에서 이 것을 나타낼 방법이 없습니다. 다음 두 가지 중 하나를 수행할 수 있습니다.

- 사용자에게 이전 버전을 제거하고 새 위치에서 새 버전을 설치하도록 지시합니다.

- 에 대한 `http://www.adatum.com/MyApplication/` 포인팅을 `deploymentProvider` `http://www.adatum.com/MyApplication/`포함하는 업데이트를 포함합니다. 그런 다음 나중에 을 `deploymentProvider` 가리키면서 다른 업데이트를 릴리스합니다. `http://subdomain.adatum.com/MyApplication/`

  두 번째 예제에서는 `deploymentProvider`을 지정하는 ClickOnce 응용 프로그램을 게시한 다음 제거하기로 결정합니다. 클라이언트에 다운로드되지 `deploymentProvider` 않은 새 버전이 다운로드되면 `deploymentProvider` 복원된 응용 프로그램의 버전을 릴리스할 때까지 업데이트에 사용된 경로를 리디렉션할 수 없습니다. 첫 번째 예제와 `deploymentProvider` 마찬가지로 처음에는 새 위치가 아닌 현재 업데이트 위치를 가리가야 합니다. 이 경우 `deploymentProvider` `http://subdomain.adatum.com/MyApplication/`을 참조하는 를 삽입하려고 하면 다음 업데이트가 실패합니다.

## <a name="create-a-deployment"></a>배포 만들기
 다른 네트워크 위치에서 배포할 수 있는 배포를 만드는 단계별 지침은 [연습: 다시 서명할 필요가 없고 브랜딩 정보를 보존하는 ClickOnce 응용 프로그램을 수동으로 배포하는 경우를](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)참조하십시오.

## <a name="see-also"></a>참고 항목
- [*Mage.exe* (매니페스트 생성 및 편집 도구)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (매니페스트 생성 및 편집 도구, 그래픽 클라이언트)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
