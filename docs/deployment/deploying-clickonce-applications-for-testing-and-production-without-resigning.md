---
title: 다시 서명 하지 않고 ClickOnce 앱 배포
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395329"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>다시 서명 하지 않고 테스트 및 프로덕션 서버용 ClickOnce 응용 프로그램 배포
이 문서에서는 clickonce 매니페스트를 다시 서명 하거나 변경 하지 않고 여러 네트워크 위치에서 ClickOnce 응용 프로그램을 배포할 수 있도록 하는 .NET Framework 버전 3.5에 도입 된 ClickOnce 기능을 설명 합니다.

> [!NOTE]
> 다시 서명는 새 버전의 응용 프로그램을 배포 하는 데 여전히 선호 되는 방법입니다. 가능 하면 다시 서명 메서드를 사용 합니다. 자세한 내용은 [ *Mage.exe* (매니페스트 생성 및 편집 도구)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)를 참조 하세요.

 타사 개발자 및 Isv는이 기능을 옵트인 (opt in) 하 여 고객이 응용 프로그램을 더 쉽게 업데이트할 수 있게 해줍니다. 이 기능은 다음과 같은 경우에 사용할 수 있습니다.

- 응용 프로그램을 업데이트 하는 경우 응용 프로그램을 처음 설치 하는 경우입니다.

- 컴퓨터에 응용 프로그램 구성이 하나만 있는 경우 예를 들어 응용 프로그램이 서로 다른 두 데이터베이스를 가리키도록 구성 된 경우에는이 기능을 사용할 수 없습니다.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>배포 매니페스트에서 deploymentProvider 제외
 .NET Framework 2.0 및 .NET Framework 3.0에서 오프 라인으로 가용성을 위해 시스템에를 설치 하는 모든 ClickOnce 응용 프로그램은 배포 매니페스트에을 나열 해야 합니다 `deploymentProvider` . 은 `deploymentProvider` 종종 업데이트 위치 라고 하며 ClickOnce에서 응용 프로그램 업데이트를 확인 하는 위치입니다. 이 요구 사항은 응용 프로그램 게시자가 자신의 배포에 서명 하는 데 필요한 요구 사항과 함께 공급 업체 또는 타사에서 ClickOnce 응용 프로그램을 업데이트 하는 작업을 어렵게 만들었습니다. 또한 동일한 네트워크의 여러 위치에서 동일한 응용 프로그램을 배포 하는 것이 더 어려워집니다.

 .NET Framework 3.5에서 ClickOnce를 변경한 경우 타사에서 다른 조직에 ClickOnce 응용 프로그램을 제공할 수 있습니다. 그러면이 응용 프로그램을 자체 네트워크에 배포할 수 있습니다.

 이 기능을 활용 하려면 ClickOnce 응용 프로그램 개발자가 해당 배포 매니페스트에서를 제외 해야 합니다 `deploymentProvider` . 이 요구 사항은 `-providerUrl` Mage.exe를 사용 하 여 배포 매니페스트를 만들 때 인수를 제외 해야 함을 의미 합니다. 또는 MageUI.exe를 사용 하 여 배포 매니페스트를 생성 하는 경우 **응용 프로그램 매니페스트** 탭의 **시작 위치** 텍스트 상자가 비어 있는지 확인 해야 합니다.

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider 및 응용 프로그램 업데이트
 3.5 .NET Framework부터, `deploymentProvider` 온라인 및 오프 라인 사용을 위해 ClickOnce 응용 프로그램을 배포 하기 위해 더 이상 배포 매니페스트에서를 지정할 필요가 없습니다. 이 변경은 배포를 직접 패키지 하 고 서명 해야 하지만 다른 회사에서 네트워크를 통해 응용 프로그램을 배포할 수 있도록 하는 시나리오를 지원 합니다.

 기억해 야 할 중요 한 점은를 제외 하는 응용 프로그램이 `deploymentProvider` 태그를 다시 포함 하는 업데이트를 제공할 때까지 업데이트 중에 설치 위치를 변경할 수 없다는 것입니다 `deploymentProvider` .

 이 점을 명확히 하기 위한 두 가지 예는 다음과 같습니다. 첫 번째 예제에서는 태그가 없는 ClickOnce 응용 프로그램을 게시 하 `deploymentProvider` 고 사용자에 게에서 설치 하도록 요청 `http://www.adatum.com/MyApplication/` 합니다. 에서 응용 프로그램의 다음 업데이트를 게시 하려는 경우 `http://subdomain.adatum.com/MyApplication/` 에 있는 배포 매니페스트에서이를 확인할 수 있는 방법이 없습니다 `http://www.adatum.com/MyApplication/` . 다음 두 가지 작업 중 하나를 수행할 수 있습니다.

- 사용자에 게 이전 버전을 제거 하도록 지시 하 고 새 위치에서 새 버전을 설치 합니다.

- `http://www.adatum.com/MyApplication/`을 가리키는를 포함 하는에 대 한 업데이트를 포함 `deploymentProvider` `http://www.adatum.com/MyApplication/` 합니다. 그런 다음를 가리켜 나중에 다른 업데이트를 해제 `deploymentProvider` `http://subdomain.adatum.com/MyApplication/` 합니다.

  두 번째 예제에서는를 지정 하는 ClickOnce 응용 프로그램을 게시 한 `deploymentProvider` 다음 제거 하도록 결정 합니다. 를 사용 하지 않고 새 버전을 클라이언트에 다운로드 한 후에는 `deploymentProvider` 복원 된 응용 프로그램 버전을 릴리스할 때까지 업데이트에 사용 되는 경로를 리디렉션할 수 없습니다 `deploymentProvider` . 첫 번째 예제와 마찬가지로는 `deploymentProvider` 처음에는 새 위치가 아니라 현재 업데이트 위치를 가리켜야 합니다. 이 경우를 참조 하는를 삽입 하려고 하면 `deploymentProvider` `http://subdomain.adatum.com/MyApplication/` 다음 업데이트가 실패 합니다.

## <a name="create-a-deployment"></a>배포 만들기
 다른 네트워크 위치에서 배포할 수 있는 배포를 만드는 방법에 대 한 단계별 지침은 [연습: 다시 서명할 필요가 없고 브랜딩 정보를 유지 하는 ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [*Mage.exe* (매니페스트 생성 및 편집 도구)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (매니페스트 생성 및 편집 도구, 그래픽 클라이언트)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
