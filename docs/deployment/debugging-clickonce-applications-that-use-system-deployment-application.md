---
title: System.object를 사용 하는 ClickOnce 응용 프로그램 디버그
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 203f1edc2e29bbbc34fb39e6aa01c1b56bf20e91
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382655"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>System.Deployment.Application을 사용하는 ClickOnce 애플리케이션 디버그
에서 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 배포를 사용 하면 응용 프로그램을 업데이트 하는 방법을 구성할 수 있습니다. 그러나 고급 배포 기능을 사용 하 고 사용자 지정 해야 하는 경우 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 에서 제공 하는 배포 개체 모델에 액세스 해야 <xref:System.Deployment.Application> 합니다. <xref:System.Deployment.Application>다음과 같은 고급 작업에 api를 사용할 수 있습니다.

- 응용 프로그램에서 "지금 업데이트" 옵션 만들기

- 다양 한 응용 프로그램 구성 요소의 조건부, 주문형 다운로드

- 응용 프로그램에 직접 통합 된 업데이트

- 클라이언트 응용 프로그램이 항상 최신 상태를 유지 하도록 보장

  Api는 기술을 사용 하 여 <xref:System.Deployment.Application> 응용 프로그램을 배포한 경우에만 작동 하므로 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 디버그 하는 유일한 방법은를 사용 하 여 응용 프로그램을 배포 하 고 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , 연결 하 고, 디버그 하는 것입니다. 디버거를 연결 하기 전에 응용 프로그램을 시작 하 고 실행할 때이 코드가 자주 실행 되기 때문에 디버거를 빠르게 연결 하는 것은 어려울 수 있습니다. 해결 방법은 업데이트 검사 코드 또는 요청 시 코드 전에 중단 (또는 Visual Basic 프로젝트에 대 한 중지)을 수행 하는 것입니다.

  권장 디버깅 기술은 다음과 같습니다.

1. 시작 하기 전에 기호 (.pdb) 및 소스 파일이 보관 되어 있는지 확인 합니다.

2. 응용 프로그램의 버전 1을 배포 합니다.

3. 비어 있는 새 솔루션을 만듭니다. **파일** 메뉴에서 **새로 만들기**, **프로젝트**를 차례로 클릭합니다. **새 프로젝트** 대화 상자에서 **기타 프로젝트 형식** 노드를 연 다음 **Visual Studio 솔루션** 폴더를 선택 합니다. **템플릿** 창에서 **빈 솔루션**을 선택 합니다.

4. 이 새 솔루션에 대 한 속성에 보관 된 원본 위치를 추가 합니다. **솔루션 탐색기**에서 솔루션 노드를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다. **속성 페이지** 대화 상자에서 **디버그 소스 파일**을 선택 하 고 보관 된 소스 코드의 디렉터리를 추가 합니다. 그렇지 않으면 소스 파일 경로가 .pdb 파일에 기록 되므로 디버거가 오래 된 소스 파일을 찾습니다. 디버거가 오래 된 소스 파일을 사용 하는 경우 소스가 일치 하지 않는다는 메시지가 표시 됩니다.

5. 디버거가 *.pdb* 파일을 찾을 수 있는지 확인 합니다. 응용 프로그램을 사용 하 여 응용 프로그램을 배포한 경우 디버거에서 해당 파일을 자동으로 찾습니다. 이는 항상 먼저 문제의 어셈블리 옆에 표시 됩니다. 그렇지 않으면 **기호 파일 (.pdb) 위치** 에 보관 경로를 추가 해야 합니다 .이 옵션에 액세스 하려면 **도구** 메뉴에서 **옵션**을 클릭 한 다음 **디버깅** 노드를 열고 **기호**를 클릭 합니다.

6. 메서드와 메서드 호출 사이에 발생 하는 작업을 디버깅 `CheckForUpdate` `Download` / `Update` 합니다.

    예를 들어 업데이트 코드는 다음과 같을 수 있습니다.

   ```vb
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
           If My.Application.Deployment.IsNetworkDeployed Then

               If (My.Application.Deployment.CheckForUpdate()) Then

                   My.Application.Deployment.Update()
                   Application.Restart()

               End If

           End If
       End Sub
   ```

7. 버전 2를 배포 합니다.

8. 버전 2에 대 한 업데이트를 다운로드할 때 버전 1 응용 프로그램에 디버거를 연결 하려고 합니다. 또는 메서드를 사용 `System.Diagnostics.Debugger.Break` 하거나 단순히 Visual Basic에서 사용할 수 있습니다 `Stop` . 물론 이러한 메서드 호출을 프로덕션 코드에서 벗어나면 안 됩니다.

    예를 들어 Windows Forms 응용 프로그램을 개발 하 고 있고이 메서드에 대 한 이벤트 처리기가 업데이트 논리를 사용 하는 경우를 가정해 보겠습니다. 이를 디버그 하려면 단추를 누르기 전에 연결 하 고 중단점을 설정 합니다. 적절 한 보관 파일을 열고 중단점을 설정 해야 합니다.

   <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A>응용 프로그램이 배포 된 경우에만 api를 호출 하려면 속성을 사용 하 고 <xref:System.Deployment.Application> , 디버깅 중에는 api를 호출 하면 안 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 됩니다.

## <a name="see-also"></a>참조
- <xref:System.Deployment.Application>