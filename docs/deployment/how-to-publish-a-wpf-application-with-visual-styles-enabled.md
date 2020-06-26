---
title: 방법-비주얼 스타일을 사용 하 여 WPF 응용 프로그램 게시 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21c94cc7ab97070b138cbae108c617094faf09b5
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382213"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>방법: 시각적 개체 스타일을 사용하여 WPF 애플리케이션 게시

시각적 스타일을 사용 하면 사용자가 선택한 테마에 따라 공용 컨트롤의 모양을 변경할 수 있습니다. 기본적으로 비주얼 스타일은 WPF (Windows Presentation Foundation) 응용 프로그램에 대해 사용 하도록 설정 되어 있지 않으므로 수동으로 사용 하도록 설정 해야 합니다. 그러나 WPF 응용 프로그램에 비주얼 스타일을 사용 하도록 설정 하 고 솔루션을 게시 하면 오류가 발생 합니다. 이 항목에서는 비주얼 스타일을 사용 하는 WPF 응용 프로그램을 게시 하기 위한 프로세스 및이 오류를 해결 하는 방법에 대해 설명 합니다. 비주얼 스타일에 대 한 자세한 내용은 [비주얼 스타일 개요](/windows/desktop/Controls/visual-styles-overview)를 참조 하세요. 오류 메시지에 대 한 자세한 내용은 [ClickOnce 배포의 특정 오류 문제 해결](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)을 참조 하세요.

 오류를 해결 하 고 솔루션을 게시 하려면 다음 작업을 수행 해야 합니다.

- [비주얼 스타일을 사용 하지 않고 솔루션을 게시](#publish-the-solution-without-visual-styles-enabled)합니다.

- [매니페스트 파일을 만듭니다](#create-a-manifest-file).

- [게시 된 솔루션의 실행 파일에 매니페스트 파일을 포함](#embed-the-manifest-file-into-the-executable-file-of-the-published-solution)합니다.

- [응용 프로그램 및 배포 매니페스트에 서명](#sign-the-application-and-deployment-manifests)합니다.

  그런 다음 최종 사용자가 응용 프로그램을 설치 하려는 위치로 게시 된 파일을 이동할 수 있습니다.

## <a name="publish-the-solution-without-visual-styles-enabled"></a>비주얼 스타일을 사용 하지 않고 솔루션 게시

1. 프로젝트에 비주얼 스타일을 사용 하도록 설정 하지 않았는지 확인 합니다. 먼저 프로젝트의 매니페스트 파일에서 다음 XML을 확인 합니다. 그런 다음 XML이 있는 경우 주석 태그로 XML을 묶습니다.

     기본적으로 비주얼 스타일은 사용 되지 않습니다.

    ```xml
    <dependency>
        <dependentAssembly>
            <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
        </dependentAssembly>
    </dependency>
    ```

     다음 절차에서는 프로젝트와 연결 된 매니페스트 파일을 여는 방법을 보여 줍니다.

    **Visual Basic 프로젝트에서 매니페스트 파일을 열려면**

    1. 메뉴 모음에서 **프로젝트**, *projectname* **속성**을 선택 합니다. 여기서 *ProjectName* 는 WPF 프로젝트의 이름입니다.

         WPF 프로젝트에 대 한 속성 페이지가 나타납니다.

    2. **응용 프로그램** 탭에서 **Windows 설정 보기**를 선택 합니다.

         응용 프로그램 매니페스트 파일은 **코드 편집기**에서 열립니다.

    **C # 프로젝트에서 매니페스트 파일을 열려면**

    1. 메뉴 모음에서 **프로젝트**, *projectname* **속성**을 선택 합니다. 여기서 *ProjectName* 는 WPF 프로젝트의 이름입니다.

         WPF 프로젝트에 대 한 속성 페이지가 나타납니다.

    2. **응용 프로그램** 탭에서 매니페스트 필드에 표시 되는 이름을 적어 둡니다. 프로젝트와 연결 된 매니페스트의 이름입니다.

        > [!NOTE]
        > 매니페스트 필드에 **기본 설정이 있는 매니페스트 포함** 또는 **매니페스트가 없는 응용 프로그램 만들기** 가 표시 되는 경우 비주얼 스타일을 사용할 수 없습니다. 매니페스트 파일의 이름이 매니페스트 필드에 표시 되는 경우이 절차의 다음 단계를 진행 합니다.

    3. **솔루션 탐색기**에서 **모든 파일 표시**를 선택합니다.

         이 단추는 제외 된 항목 및 일반적으로 숨겨지는 항목을 포함 하 여 모든 프로젝트 항목을 표시 합니다. 매니페스트 파일은 프로젝트 항목으로 표시 됩니다.

2. 솔루션을 빌드 및 게시 합니다. 솔루션을 게시 하는 방법에 대 한 자세한 내용은 [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)를 참조 하세요.

## <a name="create-a-manifest-file"></a>매니페스트 파일 만들기

1. 다음 XML을 메모장 파일에 붙여 넣습니다.

     이 XML에서는 비주얼 스타일을 지 원하는 컨트롤을 포함 하는 어셈블리에 대해 설명 합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <asmv1:assembly manifestVersion="1.0"
        xmlns="urn:schemas-microsoft-com:asm.v1"
        xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
        xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <dependency>
            <dependentAssembly>
                <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
            </dependentAssembly>
        </dependency>
    </asmv1:assembly>
    ```

2. 메모장에서 **파일**을 클릭 한 다음 다른 **이름으로 저장**을 클릭 합니다.

3. 다른 이름 **으로 저장** 대화 상자의 파일 **형식** 드롭다운 목록에서 **모든 파일**을 선택 합니다.

4. **파일 이름 상자에서** 파일 이름을 파일 이름 끝에 추가 하 고 .manifest를 추가 *합니다* . 예: *themes*.

5. **폴더 찾아보기** 단추를 선택 하 고 폴더를 선택한 다음 **저장**을 클릭 합니다.

    > [!NOTE]
    > 나머지 절차에서는이 파일의 이름이 *themes* 이 고 파일이 컴퓨터의 *C:\temp* 디렉터리에 저장 되어 있다고 가정 합니다.

## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a>게시 된 솔루션의 실행 파일에 매니페스트 파일 포함

1. **Visual Studio 명령 프롬프트**를 엽니다.

    **Visual Studio 명령 프롬프트**를 여는 방법에 대 한 자세한 내용은 [명령 프롬프트](/dotnet/framework/tools/developer-command-prompt-for-vs)를 참조 하세요.

   > [!NOTE]
   > 나머지 단계는 솔루션에 대해 다음과 같은 가정을 합니다.
   >
   > - 솔루션 이름은 **MyWPFProject**입니다.
   > - 솔루션은 다음 디렉터리에 `%UserProfile%\Documents\Visual Studio 2010\Projects\` 있습니다.
   >
   > - 솔루션은 다음 디렉터리에 게시 `%UserProfile%\Documents\Visual Studio 2010\Projects\publish` 됩니다.
   > - 게시 된 응용 프로그램 파일의 최신 버전은 다음 디렉터리에 있습니다.`%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`
   >
   > 위에서 설명한 이름 또는 디렉터리 위치를 사용 하지 않아도 됩니다. 위에 설명 된 이름과 위치는 솔루션을 게시 하는 데 필요한 단계를 설명 하는 데만 사용 됩니다.

2. 명령 프롬프트에서 게시 된 응용 프로그램 파일의 최신 버전이 포함 된 디렉터리로 경로를 변경 합니다. 다음 예제에서는이 단계를 보여 줍니다.

   ```cmd
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"
   ```

3. 명령 프롬프트에서 다음 명령을 실행 하 여 매니페스트 파일을 응용 프로그램의 실행 파일에 포함 합니다.

   ```cmd
   mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy
   ```

## <a name="sign-the-application-and-deployment-manifests"></a>응용 프로그램 및 배포 매니페스트에 서명

1. 명령 프롬프트에서 다음 명령을 실행 하 여 현재 디렉터리에 있는 실행 파일에서 *.deploy* 확장명을 제거 합니다.

   ```cmd
   ren MyWPFApp.exe.deploy MyWPFApp.exe
   ```

   > [!NOTE]
   > 이 예에서는 하나의 파일만 *.deploy* 파일 확장명을 갖는 것으로 가정 합니다. 이 디렉터리에서 확장명이 .deploy 인 모든 파일의 이름을 변경 해야 *합니다.*

2. 명령 프롬프트에서 다음 명령을 실행 하 여 응용 프로그램 매니페스트에 서명 합니다.

   ```cmd
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > 이 예제에서는 프로젝트의 *.pfx* 파일을 사용 하 여 매니페스트에 서명 하는 것으로 가정 합니다. 매니페스트에 서명 하지 않는 경우 `-cf` 에는이 예제에 사용 된 매개 변수를 생략할 수 있습니다. 암호를 요구 하는 인증서를 사용 하 여 매니페스트에 서명 하는 경우 `-password` 옵션 ()을 지정 `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` 합니다.

3. 명령 프롬프트에서 다음 명령을 실행 하 여이 절차의 이전 단계에서 이름을 바꾼 파일의 이름에 .deploy 확장명을 추가 *합니다* .

   ```
   ren MyWPFApp.exe MyWPFApp.exe.deploy
   ```

   > [!NOTE]
   > 이 예에서는 하나의 파일만 파일 확장명이 *.deploy* 인 것으로 가정 합니다. 이전에 파일 이름 확장명이 .deploy 인이 디렉터리에 있는 모든 파일의 이름을 바꿔야 합니다 *.*

4. 명령 프롬프트에서 다음 명령을 실행 하 여 배포 매니페스트에 서명 합니다.

   ```
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > 이 예제에서는 프로젝트의 *.pfx* 파일을 사용 하 여 매니페스트에 서명 하는 것으로 가정 합니다. 매니페스트에 서명 하지 않는 경우 `-cf` 에는이 예제에 사용 된 매개 변수를 생략할 수 있습니다. 암호를 요구 하는 인증서를 사용 하 여 매니페스트에 서명 하는 경우 `-password` 이 예제와 같이 옵션을 지정 `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` 합니다.

   이러한 단계를 수행한 후에는 게시 된 파일을 최종 사용자가 응용 프로그램을 설치 하려는 위치로 이동할 수 있습니다. 솔루션을 자주 업데이트 하려는 경우 이러한 명령을 스크립트로 이동 하 고 새 버전을 게시할 때마다 스크립트를 실행할 수 있습니다.

## <a name="see-also"></a>추가 정보

-[ClickOnce 배포 관련 오류 문제 해결](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)
- [비주얼 스타일 개요](/windows/desktop/Controls/visual-styles-overview)
- [시각적 개체 스타일 사용](/windows/desktop/Controls/cookbook-overview)
- [명령 프롬프트](/dotnet/framework/tools/developer-command-prompt-for-vs)
