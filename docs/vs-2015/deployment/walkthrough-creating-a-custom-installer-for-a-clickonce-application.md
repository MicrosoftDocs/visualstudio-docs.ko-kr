---
title: '연습: ClickOnce 응용 프로그램에 대 한 사용자 지정 설치 관리자 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ebde75fdf36c84f40ae660a24d469c36e72ceaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842050"
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>연습: ClickOnce 애플리케이션용 사용자 지정 설치 관리자 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.Exe 파일을 기반으로 하는 모든 ClickOnce 응용 프로그램은 사용자 지정 설치 관리자에서 자동으로 설치 및 업데이트할 수 있습니다. 사용자 지정 설치 관리자는 보안 및 유지 관리 작업을 위한 사용자 지정 대화 상자를 포함 하 여 설치 중에 사용자 지정 사용자 환경을 구현할 수 있습니다. 설치 작업을 수행 하기 위해 사용자 지정 설치 관리자는 클래스를 사용 합니다 <xref:System.Deployment.Application.InPlaceHostingManager> . 이 연습에서는 ClickOnce 응용 프로그램을 자동으로 설치 하는 사용자 지정 설치 관리자를 만드는 방법을 보여 줍니다.  
  
## <a name="prerequisites"></a>전제 조건  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>사용자 지정 ClickOnce 응용 프로그램 설치 관리자를 만들려면  
  
1. ClickOnce 응용 프로그램에서 System.object에 대 한 참조를 추가 합니다.  
  
2. 응용 프로그램에 새 클래스를 추가 하 고 이름을 지정 합니다. 이 연습에서는 `MyInstaller`라는 이름을 사용합니다.  
  
3. `Imports` `using` 새 클래스의 맨 위에 다음 또는 문을 추가 합니다.  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4. 클래스에 다음 메서드를 추가 합니다.  
  
     이러한 메서드는 <xref:System.Deployment.Application.InPlaceHostingManager> 메서드를 호출 하 여 배포 매니페스트를 다운로드 하 고, 적절 한 권한을 어설션 하며, 사용자에 게 설치 권한을 요청 하 고, ClickOnce 캐시에 응용 프로그램을 다운로드 하 여 설치 합니다. 사용자 지정 설치 관리자는 ClickOnce 응용 프로그램이 미리 신뢰 되도록 지정 하거나 메서드 호출에 대 한 트러스트 결정을 연기할 수 있습니다 <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> . 이 코드는 응용 프로그램을 미리 신뢰 합니다.  
  
    > [!NOTE]
    > 미리 트러스팅에서 할당 한 사용 권한은 사용자 지정 설치 관리자 코드의 사용 권한을 초과할 수 없습니다.  
  
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs#1)]
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb#1)]  
  
5. 코드에서 설치를 시도 하려면 메서드를 호출 `InstallApplication` 합니다. 예를 들어 클래스의 이름을 지정 하는 경우 `MyInstaller` 다음과 같은 방식으로를 호출할 수 있습니다 `InstallApplication` .  
  
    ```vb  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```csharp  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
    ```  
  
## <a name="next-steps"></a>다음 단계  
 ClickOnce 응용 프로그램은 업데이트 프로세스 중에 표시할 사용자 지정 사용자 인터페이스를 비롯 한 사용자 지정 업데이트 논리를 추가할 수도 있습니다. 자세한 내용은 <xref:System.Deployment.Application.UpdateCheckInfo>를 참조하세요. ClickOnce 응용 프로그램은 요소를 사용 하 여 표준 시작 메뉴 항목, 바로 가기 및 프로그램 추가/제거 항목을 표시 하지 않을 수도 있습니다 `<customUX>` . 자세한 내용은 [ \<entryPoint> 요소](../deployment/entrypoint-element-clickonce-application.md) 및을 참조 하십시오 <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A> .  
  
## <a name="see-also"></a>참고 항목  
 [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint> 요소](../deployment/entrypoint-element-clickonce-application.md)
