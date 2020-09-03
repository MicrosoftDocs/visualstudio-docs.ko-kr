---
title: DLL 프로젝트 디버깅 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4a4533c304f84d9dc59ec6b05328528870e49655
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691392"
---
# <a name="debugging-dll-projects"></a>DLL 프로젝트 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DLL을 만드는 템플릿은 다음과 같습니다.  
  
- (C++, C# 및 Visual Basic): 클래스 라이브러리  
  
- (C++, C# 및 Visual Basic): Windows Forms 컨트롤 라이브러리  
  
   Windows 컨트롤 라이브러리는 클래스 라이브러리 프로젝트와 비슷한 방법으로 디버깅할 수 있습니다. 대부분의 경우에 다른 프로젝트에서 Windows 컨트롤을 호출하게 됩니다. 따라서 호출하는 프로젝트를 디버깅할 때 Windows 컨트롤의 코드를 단계별로 실행하고, 중단점을 설정하고, 다른 디버깅 작업을 수행할 수 있습니다. 자세한 내용은 [Windows Forms 컨트롤](https://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)을 참조하십시오.  
  
- (C# 및 Visual Basic): 웹 컨트롤 라이브러리  
  
   자세한 내용은 [Web Control Library (Managed Code)](../debugger/web-control-library-managed-code.md)을 참조하십시오.  
  
- (C++): MFC ActiveX 컨트롤 및 MFC 스마트 디바이스 ActiveX 컨트롤  
  
   ActiveX 컨트롤은 인터넷을 통해 클라이언트 컴퓨터에 다운로드하여 웹 페이지에 표시 및 활성화할 수 있는 컨트롤입니다.  
  
   독립적으로 실행할 수 없고 HTML 웹 페이지에 포함되어야 한다는 점에서 ActiveX 컨트롤을 디버깅하는 방식은 다른 종류의 컨트롤을 디버깅하는 방식과 비슷합니다. 자세한 내용은 [How to: Debug an ActiveX Control](../debugger/how-to-debug-an-activex-control.md)을 참조하십시오.  
  
- (C++): MFC 스마트 디바이스 DLL  
  
   자세한 내용은 [MFC 디버깅 기술](../debugger/mfc-debugging-techniques.md)을 참조 하세요.  
  
  이 단원에서는 다음 항목에 대한 정보도 제공합니다.  
  
- [방법: DLL 프로젝트에서 디버그](../debugger/how-to-debug-from-a-dll-project.md)  
  
- [방법: 혼합 모드에서 디버그](../debugger/how-to-debug-in-mixed-mode.md)  
  
  이 항목의 다음 단원에서는 클래스 라이브러리에 대한 디버깅을 준비하는 방법에 대해 설명합니다.  
  
- [디버그 버전 빌드](#vxtskdebuggingdllprojectsbuildingadebugversion)  
  
- [혼합 모드 디버깅](#vxtskdebuggingdllprojectsmixedmodedebugging)  
  
- [기본 구성 변경](#vxtskdebuggingdllprojectschangingdefaultconfigurations)  
  
- [DLL을 디버깅 하는 방법](#vxtskdebuggingdllprojectswaystodebugthedll)  
  
- [호출 애플리케이션](#vxtskdebuggingdllprojectsthecallingapplication)  
  
- [웹 페이지의 컨트롤](#vxtskdebuggingdllprojectscontrolsonawebpage)  
  
- [직접 실행 창](#vxtskdebuggingdllprojectstheimmediatewindow)  
  
## <a name="building-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> 디버그 버전 빌드  
 어떤 방법으로 디버깅을 시작하든지 먼저 DLL의 디버그 버전을 빌드하여 애플리케이션에서 검색할 위치에 저장해야 합니다. 만약 이 단계를 생략하면 애플리케이션에서는 다른 DLL 버전을 찾아서 로드할 수 있습니다. 그러면 프로그램은 계속 실행되지만 중단점에는 도달하지 않습니다. 디버깅 작업을 수행할 때 디버거의 **모듈** 창을 열어 프로그램에서 로드한 DLL을 확인할 수 있습니다. **모듈** 창에는 디버깅 중인 프로세스에서 로드한 각 DLL 또는 EXE가 표시됩니다. 자세한 내용은 [방법: 모듈 창 사용](../debugger/how-to-use-the-modules-window.md)을 참조 하세요.  
  
 디버거에서 C++로 작성된 코드에 연결하려면 코드에서 `DebuggableAttribute`를 내보내야 합니다. 이 특성은 [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) 링커 옵션으로 링크하여 자동으로 코드에 추가할 수 있습니다.  
  
## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> 혼합 모드 디버깅  
 DLL을 호출하는 호출 애플리케이션은 관리 코드로 작성될 수도 있고 네이티브 코드로 작성될 수도 있습니다. 네이티브 코드가 관리되는 DLL을 호출하고 두 코드를 모두 디버깅해야 하는 경우에는 관리되는 디버거와 네이티브 디버거를 모두 활성화해야 합니다. ** \<Project> 속성 페이지** 대화 상자 또는 창에서이를 선택할 수 있습니다. 이를 수행하는 방법은 DLL 프로젝트에서 디버깅을 시작하는지 아니면 호출 애플리케이션 프로젝트에서 디버깅을 시작하는지에 따라 달라집니다. 자세한 내용은 [방법: 혼합 모드에서 디버깅](../debugger/how-to-debug-in-mixed-mode.md)을 참조 하세요.  
  
## <a name="changing-default-configurations"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> 기본 구성 변경  
 프로젝트 템플릿을 사용하여 콘솔 애플리케이션 프로젝트를 만들면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에서는 디버그 및 릴리스 구성에 필요한 설정을 자동으로 만듭니다. 필요하면 이 설정을 변경할 수 있습니다. 자세한 내용은 [c + + 디버그 구성에 대 한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md), [c # 디버그](../debugger/project-settings-for-csharp-debug-configurations.md)구성에 대 한 프로젝트 설정, [Visual Basic 디버그 구성에 대 한 프로젝트](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)설정 및 [방법: 디버그 및 릴리스 구성 설정](../debugger/how-to-set-debug-and-release-configurations.md)을 참조 하세요.  
  
## <a name="ways-to-debug-the-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> DLL을 디버깅 하는 방법  
 이 단원의 각 프로젝트에서는 DLL을 만듭니다. DLL은 직접 실행할 수 없습니다. DLL은 일반적으로 EXE와 같은 애플리케이션에서 호출해야 합니다. 자세한 내용은 [Creating and Managing Visual C++ Projects](https://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047)을 참조하세요. 호출 애플리케이션은 다음 기준 중 하나에 부합해야 합니다.  
  
- 동일한 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션에서 클래스 라이브러리를 포함한 다른 프로젝트에 내장된 애플리케이션  
  
- 테스트 컴퓨터나 프로덕션 컴퓨터에 이미 배포된 기존 애플리케이션  
  
- 웹에 설치되어 URL을 통해 액세스할 수 있는 응용 프로그램  
  
- DLL을 포함하는 웹 페이지가 들어 있는 웹 애플리케이션  
  
### <a name="debugging-the-calling-application"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a> 호출 응용 프로그램 디버깅  
 DLL을 디버깅하려면 호출 애플리케이션 디버깅을 먼저 시작해야 합니다. 호출 애플리케이션은 일반적으로 EXE 또는 웹 애플리케이션입니다. 이를 디버깅하는 데는 여러 가지 방법이 있습니다.  
  
- 호출 애플리케이션에 대한 프로젝트가 있으면 이 프로젝트를 열고 **디버그** 메뉴에서 실행 파일을 시작할 수 있습니다. 자세한 내용은 [How to: Start Execution](https://msdn.microsoft.com/b0fe0ce5-900e-421f-a4c6-aa44ddae453c)을 참조하세요.  
  
- 호출 애플리케이션이 테스트 컴퓨터나 프로덕션 컴퓨터에 이미 배포되어 실행되고 있는 기존의 프로그램인 경우 이 애플리케이션에 연결할 수 있습니다. DLL이 Internet Explorer로 호스팅된 컨트롤이거나 웹 페이지의 컨트롤인 경우 이 방법을 사용합니다. 자세한 내용은 [방법: 실행 중인 프로세스에 연결](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)을 참조 하세요.  
  
- DLL 프로젝트에서 이를 디버깅할 수 있습니다. 자세한 내용은 [방법: DLL 프로젝트에서 디버그](../debugger/how-to-debug-from-a-dll-project.md)를 참조 하세요.  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **직접 실행** 창에서 이를 디버깅할 수 있습니다. 이 경우 **직접 실행** 창은 애플리케이션 역할을 수행합니다.  
  
  호출 애플리케이션에 대한 디버깅을 시작하기 전에, 일반적으로 클래스 라이브러리에 중단점을 설정합니다. 자세한 내용은 [Breakpoints and Tracepoints](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)을 참조하세요. 중단점에 도달하면 각 줄의 작업을 확인하면서 코드를 단계별로 실행하여 문제를 해결할 수 있습니다. 자세한 내용은 [코드 단계별 실행 개요](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9)를 참조 하세요.  
  
### <a name="controls-on-a-web-page"></a><a name="vxtskdebuggingdllprojectscontrolsonawebpage"></a> 웹 페이지의 컨트롤  
 웹 페이지 컨트롤을 디버깅하려면 컨트롤을 포함하는 페이지가 없는 경우 컨트롤을 포함하는 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 페이지를 만듭니다. 그런 다음 컨트롤 코드 및 웹 페이지 코드에 중단점을 배치합니다. 중단점을 설정한 후 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 웹 페이지를 호출합니다.  
  
 호출 애플리케이션에 대한 디버깅을 시작하기 전에, 일반적으로 DLL에 중단점을 설정합니다. 중단점에 도달하면 각 줄의 작업을 확인하면서 코드를 단계별로 실행하여 문제를 해결할 수 있습니다. 자세한 내용은 [Breakpoints and Tracepoints](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)을 참조하세요.  
  
### <a name="the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> 직접 실행 창  
 호출 애플리케이션을 사용하지 않고도 DLL의 함수 및 메서드를 실행할 수 있습니다. 디자인 타임 디버깅을 수행하고 **직접 실행** 창을 사용할 수 있습니다. 이러한 방식으로 디버깅하려면 DLL 프로젝트가 열려 있는 상태에서 다음 단계를 수행합니다.  
  
1. 디버거 **직접 실행** 창을 엽니다.  
  
2. `Test` 클래스의 `Class1`라는 메서드를 테스트하려면 직접 실행 창에 다음 C# 코드를 입력하여 `Class1` 형식의 개체를 인스턴스화합니다. 구문을 적절하게 변경하면 이 관리 코드는 Visual Basic 및 C++에서 작동합니다.  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     C#에서 모든 이름은 정규화되어야 합니다. 또한 모든 메서드나 변수는 디버깅 세션의 현재 범위와 컨텍스트에 있어야 합니다.  
  
3. `Test` 에서 `int` 매개 변수 하나를 사용하는 것으로 가정하고 `Test` 직접 실행 **창을 사용하여** 를 실행합니다.  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     **직접 실행** 창에 결과가 출력됩니다.  
  
4. `Test` 내에 중단점을 배치한 다음 함수를 다시 실행하여 이 메서드를 계속 디버깅할 수 있습니다.  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     중단점에 도달하면 `Test`를 단계별로 실행할 수 있습니다. `Test`실행을 마치면 디버거가 디자인 모드로 되돌아갑니다.  
  
## <a name="see-also"></a>관련 항목  
 [관리 코드 디버깅](../debugger/debugging-managed-code.md)   
 [Visual C++ 프로젝트 형식](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C #, F # 및 Visual Basic 프로젝트 형식](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C + + 디버그 구성에 대 한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C # 디버그 구성에 대 한 프로젝트 설정](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic 디버그 구성에 대 한 프로젝트 설정](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [디버거 보안](../debugger/debugger-security.md)
