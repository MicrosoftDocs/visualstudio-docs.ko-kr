---
title: 문제 해결 및 알려진 문제(Visual Studio Tools for Unity) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: troubleshooting
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: ad085cc6c41714a551fbb344274e6d0f164ab67e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297660"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>문제 해결 및 알려진 문제(Visual Studio Tools for Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 섹션에서는 Visual Stuio Tools for Unity와 관련된 일반적인 문제에 대한 솔루션, 알려진 문제의 설명을 찾아보고 오류를 보고하여 Visual Studio Tools for Unity를 개선하는 데 도움이 되는 방법을 알아봅니다.  
  
## <a name="troubleshooting"></a>문제 해결  
 Visual Studio Tools for Unity에 대한 몇 가지 일반적인 문제를 해결하려면 다음 섹션을 참조하세요.  
  
### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>UnityVS에서 Visual Studio Tools for Unity로 마이그레이션  
 UnityVS에서 Visual Studio Tools for Unity로 마이그레이션하려면 Unity 프로젝트에 대한 새로운 Visual Studio 솔루션을 생성해야 합니다.  
  
##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>UnityVS 1.8에서 Visual Studio Tools for Unity 1.9로 Unity 프로젝트를 마이그레이션하려면  
  
1. Unity 프로젝트에서 이전 솔루션 및 프로젝트 파일을 삭제합니다. Unity 프로젝트의 루트 디렉터리에서 Visual Studio .sln 및 .* proj 파일을 찾아 모두 삭제합니다.  
  
2. Visual Studio Tools for Unity 패키지를 Unity 프로젝트로 가져옵니다. VSTU 패키지를 가져오는 방법에 대한 자세한 내용은 [시작](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) 페이지에서 Visual Studio Tools for Unity 구성을 참조하세요.  
  
3. 새 솔루션 및 프로젝트 파일을 생성합니다. 지금 생성하려면 Unity 편집기의 주 메뉴에서 **Visual Studio Tools**, **프로젝트 파일 생성**을 선택합니다. 그렇지 않으면 원하는 경우 이 단계를 건너뛸 수 있습니다. **Visual Studio Tools**, **Visual Studio에서 열기**를 선택하면 Visual Studio Tools for Unity에서 새 파일을 자동으로 생성합니다.  
  
### <a name="visual-studio-wont-load-the-solution-that-visual-studio-tools-for-unity-created"></a>Visual Studio는 Visual Studio Tools for Unity에서 만든 솔루션을 로드하지 않습니다.  
 자세한 내용은 [the answer to this stackoverflow question(이 stackoverflow 질문의 답변)](https://stackoverflow.com/questions/20086755/unityvs-visual-studio-can-not-open/24035907#24035907)을 참조하세요.  
  
### <a name="on-windows-8-visual-studio-asks-to-download-the-unity-target-framework"></a>Windows 8에서 Visual Studio는 Unity 대상 프레임워크 다운로드를  요청합니다.  
 UnityVS를 사용하려면 Windows 8에 기본적으로 설치되지 않는 .net framework 3.5가 필요합니다. 이 문제를 해결하려면 지침에 따라 .net framework 3.5를 다운로드하고 설치하세요.  
  
## <a name="known-issues"></a>알려진 문제  
 Visual Studio Tools for Unity에는 디버거가 C# 컴파일러의 Unity 이전 버전과 상호작용하는 방법에서 발생하는 알려진 문제가 있습니다. 문제를 해결하기 위해 노력 중이지만 해결하기 전까지는 다음과 같은 문제가 발생할 수 있습니다.  
  
- 디버그할 때 Unity가 충돌되는 경우가 있습니다.  
  
- 디버그할 때 Unity가 중지되는 경우가 있습니다.  
  
- 특히 반복기 또는 switch 문 내에서 경우에 따라 메서드를 한 단계씩 코드 실행하고 메서드의 프로시저에서 나가는 동작이 제대로 작동하지 않습니다.  
  
## <a name="reporting-errors"></a>오류 보고  
 충돌, 고정 또는 기타 오류가 발생하는 경우 오류 보고서를 전송하여 Visual Studio Tools for Unity의 품질을 개선할 수 있도록 도와주시기 바랍니다. Visual Studio Tools for Unity의 문제를 조사하고 해결하는 데 도움이 됩니다. 감사합니다!  
  
### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Visual Studio가 고정될 때 오류를 보고하는 방법  
 Visual Studio가 Visual Studio Tools for Unity로 디버그할 때 중지되는 경우가 있다는 보고가 있지만 이 문제를 파악하려면 더 많은 데이터가 필요합니다. 아래의 단계를 따라 이 문제를 조사하는 데 도움을 주실 수 있습니다.  
  
##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Visual Studio가 Visual Studio Tools for Unity로 디버그할 때 중지되는 문제를 보고하려면  
  
1. 새 Visual Studio 인스턴스를 엽니다.  
  
2. 프로세스에 연결 대화 상자를 엽니다. Visual Studio의 새 인스턴스에 있는 주 메뉴에서 **디버그**, **프로세스에 연결**을 선택합니다.  
  
3. Visual Studio의 중지된 인스턴스에 디버거를 연결합니다. **프로세스에 연결** 대화 상자에서 **사용 가능한 프로세스** 테이블로부터 Visual Studio의 중지된 인스턴스를 선택한 다음 **연결** 단추를 선택합니다.  
  
4. 디버거를 일시 중지합니다. Visual Studio의 새 인스턴스에 있는 주 메뉴에서 **디버그**, **모두 중단** 을 선택 하거나 **ctrl + Alt + break**를 누릅니다.  
  
5. 스레드 덤프를 만듭니다. 명령 창에서 다음 **명령을 입력 하 고 enter 키를**누릅니다.  
  
   ```powershell  
   Debug.ListCallStack /AllThreads /ShowExternalCode  
   ```  
  
    **명령** 창이 먼저 표시되도록 해야 할 수 있습니다. Visual Studio의 주 메뉴에서 **보기**, **다른 창**, **명령 창**을 선택합니다.  
  
6. 마지막으로 Visual Studio가 중지되었을 때 수행한 작업에 대한 설명과 함께 스레드 덤프를 [vstusp@microsoft.com](mailto:vstusp@microsoft.com)으로 보냅니다.
