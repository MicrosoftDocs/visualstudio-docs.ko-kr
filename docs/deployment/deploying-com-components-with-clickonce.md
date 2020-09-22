---
title: ClickOnce를 사용 하 여 COM 구성 요소 배포 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7032ec5ae03febf6c54978020379769ac742a136
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841743"
---
# <a name="deploy-com-components-with-clickonce"></a>ClickOnce를 사용하여 COM 구성 요소 배포
레거시 COM 구성 요소의 배포는 일반적으로 어려운 작업입니다. 구성 요소를 전역적으로 등록 해야 하므로 겹치는 응용 프로그램 간에 바람직하지 않은 부작용이 발생할 수 있습니다. 이러한 상황은 일반적으로 응용 프로그램이 응용 프로그램에 완전히 격리 되거나 side-by-side 호환 되기 때문에 .NET Framework 응용 프로그램에서 문제가 되지 않습니다. Visual Studio를 사용 하면 Windows XP 이상 운영 체제에서 격리 된 COM 구성 요소를 배포할 수 있습니다.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 는 .NET 응용 프로그램을 배포 하는 쉽고 안전한 메커니즘을 제공 합니다. 그러나 응용 프로그램에서 레거시 COM 구성 요소를 사용 하는 경우 배포를 위한 추가 단계를 수행 해야 합니다. 이 항목에서는 격리 된 COM 구성 요소를 배포 하 고 네이티브 구성 요소 (예: Visual Basic 6.0 또는 Visual C++)를 참조 하는 방법에 대해 설명 합니다.

 격리 된 COM 구성 요소 배포에 대 한 자세한 내용은 [ClickOnce 및 등록이 필요 없는 com을 사용 하 여 앱 배포 간소화](https://web.archive.org/web/20050326005413/msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx)를 참조 하세요.

## <a name="registration-free-com"></a>등록이 필요 없는 COM
 등록이 필요 없는 COM은 격리 된 COM 구성 요소를 배포 하 고 활성화 하기 위한 새로운 기술입니다. 일반적으로 시스템 레지스트리에 설치 되는 모든 구성 요소의 형식 라이브러리 및 등록 정보를 응용 프로그램과 동일한 폴더에 저장 된 매니페스트 라는 XML 파일에 배치 하는 방식으로 작동 합니다.

 COM 구성 요소를 격리 하려면 개발자 컴퓨터에 등록 해야 하지만 최종 사용자의 컴퓨터에 등록 해야 하는 것은 아닙니다. COM 구성 요소를 격리 하려면 해당 참조의 **격리** 된 속성을 **True**로 설정 하기만 하면 됩니다. 기본적으로이 속성은 **False**로 설정 되어 등록 된 COM 참조로 처리 되어야 함을 나타냅니다. 이 속성이 **True**이면 빌드 시이 구성 요소에 대 한 매니페스트가 생성 됩니다. 또한 설치 하는 동안 해당 파일이 응용 프로그램 폴더에 복사 됩니다.

 매니페스트 생성기는 격리 된 COM 참조를 발견 하면 `CoClass` 구성 요소의 형식 라이브러리에 있는 모든 항목을 열거 하 고, 각 항목과 해당 등록 데이터를 일치 하 고, 형식 라이브러리 파일의 모든 COM 클래스에 대 한 매니페스트 정의를 생성 합니다.

## <a name="deploy-registration-free-com-components-using-clickonce"></a>ClickOnce를 사용 하 여 등록이 필요 없는 COM 구성 요소 배포
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 배포 기술은 격리 된 COM 구성 요소를 배포 하는 데 적합 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 합니다. 및 등록이 필요 없는 com에서는 배포 하기 위해 구성 요소에 매니페스트가 있어야 하기 때문입니다.

 일반적으로 구성 요소의 작성자는 매니페스트를 제공 해야 합니다. 그러나 그렇지 않은 경우에는 Visual Studio에서 COM 구성 요소에 대 한 매니페스트를 자동으로 생성할 수 있습니다. 매니페스트 생성은 게시 프로세스 중에 수행 됩니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 자세한 내용은 [ClickOnce 응용 프로그램 게시](../deployment/publishing-clickonce-applications.md)를 참조 하세요. 이 기능을 사용 하면 Visual Basic 6.0 같은 이전 개발 환경에서 작성 한 레거시 구성 요소를 활용할 수도 있습니다.

 COM 구성 요소를 배포 하는 방법에는 두 가지가 있습니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

- 부트스트래퍼를 사용 하 여 COM 구성 요소를 배포 합니다. 지원 되는 모든 플랫폼에서 작동 합니다.

- 기본 구성 요소 격리 (등록이 필요 없는 COM) 배포를 사용 합니다. 그러나이 기능은 Windows XP 이상의 운영 체제 에서만 작동 합니다.

### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>간단한 COM 구성 요소를 격리 하 고 배포 하는 예
 등록이 필요 없는 COM 구성 요소 배포를 시연 하기 위해이 예제에서는 Visual Basic 6.0를 사용 하 여 만든 격리 된 네이티브 COM 구성 요소를 참조 하는 Visual Basic에서 Windows 기반 응용 프로그램을 만들고를 사용 하 여 배포 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 합니다.

 먼저 네이티브 COM 구성 요소를 만들어야 합니다.

##### <a name="to-create-a-native-com-component"></a>네이티브 COM 구성 요소를 만들려면

1. Visual Basic 6.0를 사용 하 여 **파일** 메뉴에서 **새로 만들기**, **프로젝트**를 차례로 클릭 합니다.

2. **새 프로젝트** 대화 상자에서 **Visual Basic** 노드를 선택 하 고 **ActiveX DLL** 프로젝트를 선택 합니다. **이름** 상자에 `VB6Hello`을 입력합니다.

    > [!NOTE]
    > 등록이 필요 없는 COM에서는 ActiveX DLL 및 ActiveX 컨트롤 프로젝트 유형만 지원 됩니다. ActiveX EXE 및 ActiveX 문서 프로젝트 형식은 지원 되지 않습니다.

3. **솔루션 탐색기**에서 **Class1 .vb** 를 두 번 클릭 하 여 텍스트 편집기를 엽니다.

4. Class1에서 메서드의 생성 된 코드 뒤에 다음 코드를 추가 합니다 `New` .

    ```vb
    Public Sub SayHello()
       MsgBox "Message from the VB6Hello COM component"
    End Sub
    ```

5. 구성 요소를 빌드합니다. **빌드** 메뉴에서 **솔루션 빌드**를 클릭합니다.

> [!NOTE]
> 등록이 필요 없는 COM은 Dll 및 COM 컨트롤 프로젝트 형식만 지원 합니다. 등록이 필요 없는 COM에서 Exe를 사용할 수 없습니다.

 이제 Windows 기반 응용 프로그램을 만들고이 응용 프로그램에 COM 구성 요소에 대 한 참조를 추가할 수 있습니다.

##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>COM 구성 요소를 사용 하 여 Windows 기반 응용 프로그램을 만들려면

1. Visual Basic를 사용 하 여 **파일** 메뉴에서 **새로 만들기**, **프로젝트**를 차례로 클릭 합니다.

2. **새 프로젝트** 대화 상자에서 **Visual Basic** 노드를 선택 하 고 **Windows 응용 프로그램**을 선택 합니다. **이름** 상자에 `RegFreeComDemo`을 입력합니다.

3. **솔루션 탐색기**에서 **모든 파일 표시** 단추를 클릭 하 여 프로젝트 참조를 표시 합니다.

4. **참조** 노드를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 **참조 추가** 를 선택 합니다.

5. **참조 추가** 대화 상자에서 **찾아보기** 탭을 클릭 하 VB6Hello.dll로 이동한 다음 선택 합니다.

    참조 목록에 **VB6Hello** 참조가 표시 됩니다.

6. **도구 상자**를 가리키고 **단추** 컨트롤을 선택한 다음 **Form1** 폼으로 끕니다.

7. **속성** 창에서 단추의 **Text** 속성을 **Hello**로 설정 합니다.

8. 단추를 두 번 클릭 하 여 처리기 코드를 추가 하 고 코드 파일에서 처리기가 다음과 같이 읽도록 코드를 추가 합니다.

   ```vb
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
       Dim VbObj As New VB6Hello.Class1
       VbObj.SayHello()
   End Sub
   ```

9. 애플리케이션을 실행합니다. **디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.

   그런 다음 컨트롤을 격리 해야 합니다. 응용 프로그램에서 사용 하는 각 COM 구성 요소는 프로젝트에서 COM 참조로 표시 됩니다. 이러한 참조는 **솔루션 탐색기** 창의 **참조** 노드 아래에 표시 됩니다. **프로젝트** 메뉴에서 **참조 추가** 명령을 사용 하 여 직접 또는 ActiveX 컨트롤을 폼으로 끌어 간접적으로 참조를 추가할 수 있습니다.

   다음 단계에서는 COM 구성 요소를 격리 하 고 격리 된 컨트롤을 포함 하는 업데이트 된 응용 프로그램을 게시 하는 방법을 보여 줍니다.

##### <a name="to-isolate-a-com-component"></a>COM 구성 요소를 격리 하려면

1. **솔루션 탐색기**의 **참조** 노드에서 **VB6Hello** 참조를 선택 합니다.

2. **속성** 창에서 **Isolated** 속성의 값을 **False** 에서 **True**로 변경 합니다.

3. **빌드** 메뉴에서 **솔루션 빌드**를 클릭합니다.

   이제 F5 키를 누르면 응용 프로그램이 예상 대로 작동 하지만 이제 등록이 필요 없는 COM에서 실행 됩니다. 이를 증명 하려면 VB6Hello.dll 구성 요소의 등록을 취소 하 고 Visual Studio IDE 외부에서 RegFreeComDemo1.exe를 실행 해 보세요. 이번에는 단추를 클릭 하면 여전히 작동 합니다. 응용 프로그램 매니페스트의 이름을 일시적으로 바꾸면 다시 실패 합니다.

> [!NOTE]
> COM 구성 요소의 등록을 일시적으로 해제 하 여 해당 구성 요소의 없음을 시뮬레이션할 수 있습니다. 명령 프롬프트를 열고를 입력 하 여 시스템 폴더로 이동한 `cd /d %windir%\system32` 다음를 입력 하 여 구성 요소 등록을 취소 `regsvr32 /u VB6Hello.dll` 합니다. 을 입력 하 여 다시 등록할 수 있습니다 `regsvr32 VB6Hello.dll` .

 최종 단계는 다음을 사용 하 여 응용 프로그램을 게시 하는 것입니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>격리 된 COM 구성 요소를 사용 하 여 응용 프로그램 업데이트를 게시 하려면

1. **빌드** 메뉴에서 **RegFreeComDemo 게시**를 클릭 합니다.

    게시 마법사가 나타납니다.

2. 게시 마법사에서 로컬 컴퓨터의 디스크에서 게시 된 파일에 액세스 하 고 검사할 수 있는 위치를 지정 합니다.

3. **마침**을 클릭하여 애플리케이션을 게시합니다.

   게시 된 파일을 검사 하면 sysmon 파일이 포함 됩니다. 컨트롤은이 응용 프로그램에 완전히 격리 됩니다. 즉, 최종 사용자의 컴퓨터에 다른 버전의 컨트롤을 사용 하는 다른 응용 프로그램이 있는 경우이 응용 프로그램을 방해할 수 없습니다.

## <a name="reference-native-assemblies"></a>네이티브 어셈블리 참조
 Visual Studio는 네이티브 Visual Basic 6.0 또는 c + + 어셈블리에 대 한 참조를 지원 합니다. 이러한 참조를 네이티브 참조 라고 합니다. 해당 **파일 형식** 속성이 **네이티브** 또는 **ActiveX**로 설정 되었는지 확인 하 여 참조가 네이티브 인지 여부를 확인할 수 있습니다.

 네이티브 참조를 추가 하려면 **참조 추가** 명령을 사용 하 여 매니페스트를 찾습니다. 일부 구성 요소는 매니페스트를 DLL 내부에 저장 합니다. 이 경우 DLL 자체를 선택 하기만 하면 Visual Studio에서 구성 요소에 포함 된 매니페스트가 포함 된 것을 감지 하는 경우 네이티브 참조로 추가 합니다. Visual Studio에는 참조 된 구성 요소와 동일한 폴더에 있는 모든 종속 파일 또는 어셈블리가 자동으로 포함 됩니다.

 COM 컨트롤 격리를 사용 하면 아직 매니페스트가 없는 COM 구성 요소를 쉽게 배포할 수 있습니다. 그러나 구성 요소가 매니페스트와 함께 제공 되는 경우 매니페스트를 직접 참조할 수 있습니다. 실제로 **격리** 된 속성을 사용 하는 대신 가능 하면 구성 요소의 작성자가 제공 하는 매니페스트를 항상 사용 해야 합니다.

## <a name="limitations-of-registration-free-com-component-deployment"></a>등록이 필요 없는 COM 구성 요소 배포의 제한 사항
 등록이 필요 없는 COM은 기존 배포 기술에 비해 명확한 이점을 제공 합니다. 그러나 유의 해야 할 몇 가지 제한 사항 및 주의 사항이 있습니다. 가장 큰 제한은 Windows XP 이상 에서만 작동 한다는 것입니다. 등록이 필요 없는 COM의 구현에서는 구성 요소가 핵심 운영 체제에서 로드 되는 방식을 변경 해야 했습니다. 아쉽게도 등록이 필요 없는 COM에 대 한 하위 수준 지원 계층은 없습니다.

 일부 구성 요소는 등록이 필요 없는 COM에 적합 한 후보가 아닙니다. 다음 조건 중 하나에 해당 하는 경우 구성 요소가 적합 한 것은 아닙니다.

- 구성 요소가 out-of-process 서버입니다. EXE 서버는 지원 되지 않습니다. Dll만 지원 됩니다.

- 구성 요소가 운영 체제의 일부 이거나 XML, Internet Explorer 또는 MDAC (Microsoft Data Access Components)와 같은 시스템 구성 요소입니다. 구성 요소 작성자의 재배포 정책을 따라야 합니다. 공급 업체에 문의 하세요.

- 구성 요소는 Microsoft Office와 같은 응용 프로그램의 일부입니다. 예를 들어 Microsoft Excel 개체 모델을 격리 해서는 안 됩니다. 이는 Office의 일부 이며 전체 Office 제품이 설치 된 컴퓨터 에서만 사용할 수 있습니다.

- 구성 요소는 Office 추가 기능 또는 웹 브라우저의 컨트롤 등의 추가 기능 또는 스냅인으로 사용 하기 위한 것입니다. 이러한 구성 요소에는 일반적으로 매니페스트 자체의 범위를 벗어난 호스팅 환경에서 정의 된 일종의 등록 체계가 필요 합니다.

- 구성 요소는 시스템의 실제 또는 가상 장치 (예: 인쇄 스풀러의 장치 드라이버)를 관리 합니다.

- 구성 요소는 데이터 액세스 재배포 가능 패키지입니다. 일반적으로 데이터 응용 프로그램을 실행 하려면 별도의 데이터 액세스 재배포 가능 패키지를 설치 해야 합니다. Microsoft ADO 데이터 컨트롤, Microsoft OLE DB 또는 MDAC (Microsoft Data Access Components)와 같은 구성 요소를 격리 해서는 안 됩니다. 대신 응용 프로그램에서 MDAC 또는 SQL Server Express를 사용 하는 경우 필수 구성 요소로 설정 해야 합니다. [방법: ClickOnce 응용 프로그램을 사용 하 여 필수 구성 요소 설치를](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)참조 하세요.

  경우에 따라 구성 요소의 개발자가 등록이 필요 없는 COM을 위해이를 다시 디자인할 수 있습니다. 가능 하지 않은 경우 부트스트래퍼를 사용 하 여 표준 등록 체계를 통해 종속 된 응용 프로그램을 빌드 및 게시할 수 있습니다. 자세한 내용은 [부트스트래퍼 패키지 만들기](../deployment/creating-bootstrapper-packages.md)를 참조 하세요.

  COM 구성 요소는 응용 프로그램당 한 번만 격리할 수 있습니다. 예를 들어 동일한 응용 프로그램의 일부인 두 개의 다른 **클래스 라이브러리** 프로젝트에서 동일한 COM 구성 요소를 격리할 수 없습니다. 이렇게 하면 빌드 경고가 발생 하 고 응용 프로그램이 런타임에 로드 되지 않습니다. 이 문제를 방지 하기 위해 단일 클래스 라이브러리에서 COM 구성 요소를 캡슐화 하는 것이 좋습니다.

  응용 프로그램의 배포에 등록이 필요 하지 않더라도 개발자 컴퓨터에 COM 등록이 필요한 몇 가지 시나리오가 있습니다. `Isolated`속성을 사용 하려면 빌드 중에 매니페스트를 자동으로 생성 하기 위해 COM 구성 요소를 개발자 컴퓨터에 등록 해야 합니다. 빌드 중에 자체 등록을 호출 하는 등록 캡처 기능은 없습니다. 또한 형식 라이브러리에 명시적으로 정의 되지 않은 모든 클래스는 매니페스트에 반영 되지 않습니다. 네이티브 참조와 같이 기존 매니페스트가 포함 된 COM 구성 요소를 사용 하는 경우 개발 시 구성 요소를 등록 하지 않아도 됩니다. 그러나 구성 요소가 ActiveX 컨트롤이 고 **도구 상자** 및 Windows Forms 디자이너에 포함 하려는 경우에는 등록이 필요 합니다.

## <a name="see-also"></a>참고 항목
- [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)