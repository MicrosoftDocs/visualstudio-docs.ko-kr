---
title: '연습: 개인 정보 프롬프트를 표시 하는 사용자 지정 부트스트래퍼 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6d93d9f771da9387661603f3eb71301e9d9aead7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841675"
---
# <a name="walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt"></a>연습: 사용자 지정 부트스트래퍼를 만들어 개인 정보 취급 방침 프롬프트 표시
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

최신 파일 버전 및 어셈블리 버전이 있는 어셈블리를 사용할 수 있게 되 면 ClickOnce 응용 프로그램이 자동으로 업데이트 되도록 구성할 수 있습니다. 고객이이 동작에 동의 하는지 확인 하기 위해 개인 정보 프롬프트를 표시할 수 있습니다. 그런 다음 응용 프로그램에 자동으로 업데이트할 수 있는 권한을 부여할지 여부를 선택할 수 있습니다. 응용 프로그램을 자동으로 업데이트할 수 없는 경우에는 설치 되지 않습니다.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>필수 구성 요소  
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.  
  
- Visual Studio 2010  
  
## <a name="creating-an-update-consent-dialog-box"></a>업데이트 승인 대화 상자 만들기  
 개인 정보 프롬프트를 표시 하려면 응용 프로그램에 대 한 자동 업데이트에 동의 하도록 판독기에 요청 하는 응용 프로그램을 만듭니다.  
  
#### <a name="to-create-a-consent-dialog-box"></a>동의 대화 상자를 만들려면  
  
1. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.  
  
2. **새 프로젝트** 대화 상자에서 **Windows**를 클릭 한 다음 **windows양식 응용 프로그램**을 클릭 합니다.  
  
3. **이름**에 **ConsentDialog**를 입력 한 다음 **확인**을 클릭 합니다.  
  
4. 디자이너에서 폼을 클릭 합니다.  
  
5. **속성** 창에서 **텍스트** 속성을 **업데이트 동의 대화 상자로**변경 합니다.  
  
6. **도구 상자**에서 **모든 Windows Forms**를 확장 하 고 **레이블** 컨트롤을 폼으로 끌어 옵니다.  
  
7. 디자이너에서 레이블 컨트롤을 클릭 합니다.  
  
8. **속성** 창에서 **모양** 아래의 **텍스트** 속성을 다음과 같이 변경 합니다.  
  
    설치 하려는 응용 프로그램은 웹에서 최신 업데이트를 확인 합니다. "동의 함"을 클릭 하면 응용 프로그램에 인터넷에서 자동으로 업데이트를 확인 하 고 설치할 수 있는 권한이 부여 됩니다.  
  
9. **도구 상자**에서 **Checkbox** 컨트롤을 폼의 가운데로 끌어 옵니다.  
  
10. **속성** 창에서 **레이아웃** 아래의 **텍스트** 속성을 **동의 함**으로 변경 합니다.  
  
11. **도구 상자**에서 **단추** 컨트롤을 폼의 왼쪽 아래로 끌어 옵니다.  
  
12. **속성** 창에서 **레이아웃** 아래의 **텍스트** 속성을 변경 하 여 **계속 진행**합니다.  
  
13. **속성** 창에서 **디자인** 의 **(이름)** 속성을 **ProceedButton**로 변경 합니다.  
  
14. **도구 상자**에서 **단추** 컨트롤을 폼의 오른쪽 아래로 끌어 옵니다.  
  
15. **속성** 창에서 **레이아웃** 아래의 **텍스트** 속성을 **취소**로 변경 합니다.  
  
16. **속성** 창에서 **디자인** 의 **(이름)** 속성을 **cancelbutton**으로 변경 합니다.  
  
17. 디자이너에서 **동의 함** 확인란을 두 번 클릭 하 여 CheckedChanged 이벤트 처리기를 생성 합니다.  
  
18. Form1 코드 파일에서 CheckedChanged 이벤트 처리기에 대 한 다음 코드를 추가 합니다.  
  
     [!code-csharp[ConsentDialog#1](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#1)]
     [!code-vb[ConsentDialog#1](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#1)]  
  
19. 기본적으로 **진행** 단추를 사용 하지 않도록 클래스 생성자를 업데이트 합니다.  
  
     [!code-csharp[ConsentDialog#6](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#6)]
     [!code-vb[ConsentDialog#6](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#6)]  
  
20. Form1 코드 파일에서 부울 변수에 대 한 다음 코드를 추가 하 여 최종 사용자가 온라인 업데이트로 동의한 여부를 추적 합니다.  
  
     [!code-csharp[ConsentDialog#3](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#3)]
     [!code-vb[ConsentDialog#3](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#3)]  
  
21. 디자이너에서 **계속** 단추를 두 번 클릭 하 여 click 이벤트 처리기를 생성 합니다.  
  
22. Form1 코드 파일에서 다음 코드를 클릭 하 여 **계속** 단추에 대 한 click 이벤트 처리기에 추가 합니다.  
  
     [!code-csharp[ConsentDialog#2](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#2)]
     [!code-vb[ConsentDialog#2](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#2)]  
  
23. 디자이너에서 **취소** 단추를 두 번 클릭 하 여 click 이벤트 처리기를 생성 합니다.  
  
24. Form1 코드 파일에서 **취소** 단추에 대 한 Click 이벤트 처리기에 대 한 다음 코드를 추가 합니다.  
  
     [!code-csharp[ConsentDialog#4](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/form1.cs#4)]
     [!code-vb[ConsentDialog#4](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/form1.vb#4)]  
  
25. 최종 사용자가 온라인 업데이트에 동의 하지 않을 경우 오류를 반환 하도록 응용 프로그램을 업데이트 합니다.  
  
     Visual Basic 개발자 용:  
  
    1. **솔루션 탐색기**에서 **ConsentDialog**을 클릭 합니다.  
  
    2. **프로젝트** 메뉴에서 **모듈 추가**를 클릭 한 다음 **추가**를 클릭 합니다.  
  
    3. Module1.vb 코드 파일에서 다음 코드를 추가 합니다.  
  
        [!code-vb[ConsentDialog#7](../snippets/visualbasic/VS_Snippets_ProTools/consentdialog/vb/module1.vb#7)]  
  
    4. **프로젝트** 메뉴에서 **ConsentDialog 속성**을 클릭 한 다음 **응용 프로그램** 탭을 클릭 합니다.  
  
    5. **응용 프로그램 프레임 워크 사용**을 선택 취소 합니다.  
  
    6. **시작 개체** 드롭다운 메뉴에서 **Module1**을 선택 합니다.  
  
       > [!NOTE]
       > 응용 프로그램 프레임 워크를 사용 하지 않도록 설정 하면 Windows XP 비주얼 스타일, 응용 프로그램 이벤트, 시작 화면, 단일 인스턴스 응용 프로그램 등과 같은 기능을 사용할 수 없습니다. 자세한 내용은 [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)을 참조하세요.  
  
       Visual c # 개발자 전용:  
  
       Program.cs 코드 파일을 열고 다음 코드를 추가 합니다.  
  
       [!code-csharp[ConsentDialog#5](../snippets/csharp/VS_Snippets_ProTools/consentdialog/cs/program.cs#5)]  
  
26. **빌드** 메뉴에서 **BuildSolution**를 클릭 합니다.  
  
## <a name="creating-the-custom-bootstrapper-package"></a>사용자 지정 부트스트래퍼 패키지 만들기  
 최종 사용자에 게 개인 정보 프롬프트를 표시 하려면 업데이트 동의 대화 상자 응용 프로그램에 대 한 사용자 지정 부트스트래퍼 패키지를 만들고 모든 ClickOnce 응용 프로그램에 필수 구성 요소로 포함 합니다.  
  
 이 절차에서는 다음 문서를 만들어 사용자 지정 부트스트래퍼 패키지를 만드는 방법을 보여 줍니다.  
  
- 부트스트래퍼의 콘텐츠를 설명 하는 product.xml 매니페스트 파일입니다.  
  
- 문자열, 소프트웨어 사용 조건 등 패키지의 지역화 관련 측면을 나열 하는 package.xml 매니페스트 파일입니다.  
  
- 소프트웨어 사용 조건에 대 한 문서입니다.  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>1 단계: 부트스트래퍼 디렉터리 만들기  
  
1. %PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.에 **UpdateConsentDialog** 라는 디렉터리를 만듭니다.  
  
    > [!NOTE]
    > 이 폴더를 만들려면 관리자 권한이 필요할 수 있습니다.  
  
2. UpdateConsentDialog 디렉터리에서 en 이라는 하위 디렉터리를 만듭니다.  
  
    > [!NOTE]
    > 각 로캘에 대 한 새 디렉터리를 만듭니다. 예를 들어 fr 및 de 로캘에 대 한 하위 디렉터리를 추가할 수 있습니다. 이러한 디렉터리에는 프랑스어 및 독일어 문자열과 언어 팩 (필요한 경우)이 포함 됩니다.  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>2 단계: product.xml 매니페스트 파일 만들기  
  
1. 이라는 텍스트 파일을 만듭니다 `product.xml` .  
  
2. product.xml 파일에서 다음 XML 코드를 추가 합니다. 기존 XML 코드를 덮어쓰지 않도록 해야 합니다.  
  
    ```  
    <Product  
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      ProductCode="Microsoft.Sample.EULA">  
      <!-- Defines the list of files to be copied on build. -->  
      <PackageFiles CopyAllPackageFiles="false">  
        <PackageFile Name="ConsentDialog.exe"/>  
      </PackageFiles>  
  
      <!-- Defines how to run the Setup package.-->  
      <Commands >  
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>  
          <ExitCodes>  
            <ExitCode Value="0" Result="Success" />  
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />  
            <DefaultExitCode Result="Fail"   
              FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
      </Commands>  
  
    </Product>  
    ```  
  
3. UpdateConsentDialog 부트스트래퍼 디렉터리에 파일을 저장 합니다.  
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>3 단계: package.xml 매니페스트 파일 및 소프트웨어 사용 조건 만들기  
  
1. 이라는 텍스트 파일을 만듭니다 `package.xml` .  
  
2. package.xml 파일에서 다음 XML 코드를 추가 하 여 로캘을 정의 하 고 소프트웨어 사용 조건을 포함 합니다. 기존 XML 코드를 덮어쓰지 않도록 해야 합니다.  
  
    ```  
    <Package   
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      Name="DisplayName"  
      Culture="Culture"  
      LicenseAgreement="eula.rtf">  
      <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
      </PackageFiles>  
  
      <!-- Defines a localizable string table for error messages. -->  
      <Strings>  
        <String Name="DisplayName">Update Consent Dialog</String>  
        <String Name="Culture">en</String>  
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>  
      </Strings>  
    </Package>  
    ```  
  
3. UpdateConsentDialog 부트스트래퍼 디렉터리의 en 하위 디렉터리에 파일을 저장 합니다.  
  
4. 소프트웨어 사용 조건에 대해 eula. .rtf 라는 문서를 만듭니다.  
  
    > [!NOTE]
    > 소프트웨어 사용 조건에는 라이선스, 보증, 부채 및 지방 법률에 대 한 정보가 포함 되어야 합니다. 이러한 파일은 로캘별로 지정 해야 하므로 MBCS 또는 유니코드 문자를 지 원하는 형식으로 파일을 저장 해야 합니다. 소프트웨어 사용 조건의 콘텐츠에 대 한 법률 부서에 문의 하세요.  
  
5. 문서를 UpdateConsentDialog 부트스트래퍼 디렉터리의 en 하위 디렉터리에 저장 합니다.  
  
6. 필요한 경우 각 로캘의 소프트웨어 사용 조건에 대 한 새 package.xml 매니페스트 파일 및 새 eula .rtf 문서를 만듭니다. 예를 들어 fr 및 de 로캘에 대 한 하위 디렉터리를 만든 경우 별도의 package.xml 매니페스트 파일 및 소프트웨어 사용 조건을 만들어 fr 및 de 하위 디렉터리에 저장 합니다.  
  
## <a name="setting-the-update-consent-application-as-a-prerequisite"></a>업데이트 동의 응용 프로그램을 필수 구성 요소로 설정  
 Visual Studio에서는 업데이트 동의 응용 프로그램을 필수 구성 요소로 설정할 수 있습니다.  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>업데이트 동의 응용 프로그램을 필수 구성 요소로 설정 하려면  
  
1. **솔루션 탐색기**에서 배포 하려는 응용 프로그램의 이름을 클릭 합니다.  
  
2. **프로젝트** 메뉴에서 *ProjectName* **속성**을 클릭합니다.  
  
3. **게시** 페이지를 클릭 하 고 **필수 구성 요소**를 클릭 합니다.  
  
4. **업데이트 동의 대화 상자**를 선택 합니다.  
  
    > [!NOTE]
    > 필수 구성 요소 대화 상자에서 업데이트 동의 대화 상자를 보려면 Visual Studio를 닫았다가 다시 열어야 할 수도 있습니다.  
  
5. **확인**을 클릭합니다.  
  
## <a name="creating-and-testing-the-setup-program"></a>설치 프로그램 만들기 및 테스트  
 업데이트 동의 응용 프로그램을 필수 구성 요소로 설정한 후에는 응용 프로그램에 대 한 설치 관리자 및 부트스트래퍼를 생성할 수 있습니다.  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>동의를 클릭 하지 않고 설치 프로그램을 만들고 테스트 하려면  
  
1. **솔루션 탐색기**에서 배포 하려는 응용 프로그램의 이름을 클릭 합니다.  
  
2. **프로젝트** 메뉴에서 *ProjectName* **속성**을 클릭합니다.  
  
3. **게시** 페이지를 클릭 한 다음 **지금 게시**를 클릭 합니다.  
  
4. 게시 출력이 자동으로 열리지 않으면 게시 출력으로 이동 합니다.  
  
5. Setup.exe 프로그램을 실행 합니다.  
  
     설치 프로그램에서 업데이트 동의 대화 상자 소프트웨어 사용권 계약을 표시 합니다.  
  
6. 소프트웨어 사용권 계약을 읽은 다음 **동의**를 클릭 합니다.  
  
     업데이트 동의 대화 상자 응용 프로그램이 나타나고 다음 텍스트가 표시 됩니다. 설치 하려는 응용 프로그램은 웹에서 최신 업데이트를 확인 합니다. 동의 함을 클릭 하면 인터넷에서 자동으로 업데이트를 확인 하도록 응용 프로그램에 권한을 부여 합니다.  
  
7. 응용 프로그램을 닫거나 취소를 클릭 합니다.  
  
     응용 프로그램에 오류가 표시 됩니다. *ApplicationName*에 대 한 시스템 구성 요소를 설치 하는 동안 오류가 발생 했습니다. 모든 시스템 구성 요소가 성공적으로 설치 될 때까지 설치를 계속할 수 없습니다.  
  
8. [세부 정보]를 클릭 하 여 다음 오류 메시지를 표시 합니다. "자동 업데이트 계약이 수락 되지 않았습니다." 라는 오류 메시지가 표시 되 면 구성 요소 업데이트 동의 대화 상자를 설치 하지 못했습니다. 다음 구성 요소를 설치 하지 못했습니다.-업데이트 승인 대화 상자  
  
9. **닫기**를 클릭합니다.  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>동의 함을 클릭 하 여 설치 프로그램을 만들고 테스트 하려면  
  
1. **솔루션 탐색기**에서 배포 하려는 응용 프로그램의 이름을 클릭 합니다.  
  
2. **프로젝트** 메뉴에서 *ProjectName* **속성**을 클릭합니다.  
  
3. **게시** 페이지를 클릭 한 다음 **지금 게시**를 클릭 합니다.  
  
4. 게시 출력이 자동으로 열리지 않으면 게시 출력으로 이동 합니다.  
  
5. Setup.exe 프로그램을 실행 합니다.  
  
     설치 프로그램에서 업데이트 동의 대화 상자 소프트웨어 사용권 계약을 표시 합니다.  
  
6. 소프트웨어 사용권 계약을 읽은 다음 **동의**를 클릭 합니다.  
  
     업데이트 동의 대화 상자 응용 프로그램이 나타나고 다음 텍스트가 표시 됩니다. 설치 하려는 응용 프로그램은 웹에서 최신 업데이트를 확인 합니다. 동의 함을 클릭 하면 인터넷에서 자동으로 업데이트를 확인 하도록 응용 프로그램에 권한을 부여 합니다.  
  
7. **동의 함**을 클릭 하 고 **계속**을 클릭 합니다.  
  
     응용 프로그램 설치를 시작 합니다.  
  
8. 응용 프로그램 설치 대화 상자가 표시 되 면 **설치**를 클릭 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [응용 프로그램 배포 필수 구성 요소](../deployment/application-deployment-prerequisites.md)   
 [부트스트래퍼 패키지 만들기](../deployment/creating-bootstrapper-packages.md)   
 [방법: 제품 매니페스트 만들기](../deployment/how-to-create-a-product-manifest.md)   
 [방법: 패키지 매니페스트 만들기](../deployment/how-to-create-a-package-manifest.md)   
 [제품 및 패키지 스키마 참조](../deployment/product-and-package-schema-reference.md)
