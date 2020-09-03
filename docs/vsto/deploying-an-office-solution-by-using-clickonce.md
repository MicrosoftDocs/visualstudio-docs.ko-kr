---
title: ClickOnce를 사용 하 여 Office 솔루션 배포
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f4adbd08d13d26c717beeb454bd323185bb88640
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79416564"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>ClickOnce를 사용 하 여 Office 솔루션 배포
  ClickOnce를 사용하면 Office 솔루션을 더 적은 단계로 배포할 수 있습니다. 업데이트를 게시하는 경우 솔루션에서 자동으로 이를 감지하여 설치합니다. 그러나 ClickOnce에서는 컴퓨터의 각 사용자에 대해 별도로 솔루션을 설치하도록 합니다. 따라서 둘 이상의 사용자가 동일한 컴퓨터에서 솔루션을 실행 하는 경우 Windows Installer (*.msi*)를 사용 하는 것이 좋습니다.

## <a name="in-this-topic"></a>항목 내용

- [솔루션 게시](#Publish)

- [솔루션에 신뢰를 부여하는 방법 결정](#Trust)

- [사용자의 솔루션 설치 지원](#Helping)

- [최종 사용자의 컴퓨터에 솔루션 문서 저장(문서 수준 사용자 지정에만 해당)](#Put)

- [SharePoint 실행 서버에 솔루션 문서 저장(문서 수준 사용자 지정에만 해당)](#SharePoint)

- [사용자 지정 설치 관리자 만들기](#Custom)

- [업데이트 게시](#Update)

- [솔루션의 설치 위치 변경](#Location)

- [이전 버전으로 솔루션 롤백](#Roll)

  Windows Installer 파일을 만들어 Office 솔루션을 배포 하는 방법에 대 한 자세한 내용은 [Windows Installer를 사용 하 여 office 솔루션 배포](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)를 참조 하세요.

## <a name="publish-the-solution"></a><a name="Publish"></a> 솔루션 게시
 **게시 마법사나** **프로젝트 디자이너**를 사용 하 여 솔루션을 게시할 수 있습니다. 이 절차에서는 게시 옵션의 전체 집합을 제공 하므로 **프로젝트 디자이너** 를 사용 합니다. [Visual Studio&#41;에서 Office 개발 &#40;게시 마법사를 ](../vsto/publish-wizard-office-development-in-visual-studio.md)참조 하세요.

#### <a name="to-publish-the-solution"></a>솔루션을 게시하려면

1. **솔루션 탐색기**에서 프로젝트에 대해 이름이 지정 된 노드를 선택 합니다.

2. 메뉴 모음에서 **프로젝트**, *ProjectName* **속성**을 참조하세요.

3. **프로젝트 디자이너**에서 다음 그림에 표시 된 **게시** 탭을 선택 합니다.

    ![프로젝트 디자이너의 게시 탭](../vsto/media/vsto-publishtab.png "프로젝트 디자이너의 게시 탭")

4. **게시 폴더 위치 (ftp 서버 또는 파일 경로)** 상자에 **프로젝트 디자이너** 에서 솔루션 파일을 복사할 폴더의 경로를 입력 합니다.

    다음과 같은 형식의 경로를 입력할 수 있습니다.

   - 로컬 경로 (예: *C:\folderatenameins*).

   - 네트워크의 폴더에 대 한 UNC (Uniform 명명 규칙) 경로 (예: * \\ \ServerName\FolderName*)입니다.

   - 상대 경로 (예: * \\ 프로젝트를 기본적*으로 게시 하는 폴더)입니다.

5. **설치 폴더 URL** 상자에 최종 사용자가 솔루션을 찾을 위치의 정규화 된 경로를 입력 합니다.

    위치를 아직 모를 경우이 필드에 아무것도 입력 하지 마십시오. 기본적으로 ClickOnce에서는 사용자가 솔루션을 설치한 폴더에서 업데이트를 찾습니다.

6. **필수 구성 요소** 단추를 선택합니다.

7. **필수** 구성 요소 대화 상자에서 **필수 구성 요소를 설치 하기 위한 설치 프로그램 만들기** 확인란이 선택 되어 있는지 확인 합니다.

8. **설치할 필수 구성 요소 선택** 목록에서 **Windows Installer 4.5** 및 해당 .NET Framework 패키지에 대 한 확인란을 선택 합니다.

    예를 들어 솔루션이를 대상으로 하는 경우 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] **Windows Installer 4.5** 및 **Microsoft .NET Framework 4.5 Full**의 확인란을 선택 합니다.

9. 솔루션이 .NET Framework 4.5를 대상으로 하는 경우 **Visual Studio 2010 Tools For Office Runtime** 확인란도 선택 합니다.

    > [!NOTE]
    > 이 확인란은 기본적으로 표시 되지 않습니다. 이 확인란을 표시하려면 부트스트래퍼 패키지를 만들어야 합니다. [Visual Studio 2012를 사용 하 여 Office 2013 VSTO 추가 기능 용 부트스트래퍼 패키지 만들기](create-vsto-add-ins-for-office-by-using-visual-studio.md)를 참조 하세요.

10. **필수 구성 요소의 설치 위치 지정**에서 표시 되는 옵션 중 하나를 선택한 다음 **확인** 단추를 선택 합니다.

     다음 표는 각 옵션에 대해 설명합니다.

    |옵션|설명|
    |------------|-----------------|
    |**구성 요소 공급업체의 웹 사이트에서 필수 구성 요소 다운로드**|사용자에게 공급업체로부터 이러한 필수 구성 요소를 다운로드하여 설치하라는 메시지가 나타납니다.|
    |**내 애플리케이션과 동일한 위치에서 필수 구성 요소 다운로드**|필수 구성 요소 소프트웨어가 솔루션과 함께 설치되어 있습니다. 이 옵션을 선택하면 자동으로 모든 필수 구성 요소 패키지가 게시 위치에 복사됩니다. 이 옵션이 작동하려면 필수 구성 요소 패키지가 개발 컴퓨터에 있어야 합니다.|
    |**다음 위치에서 필수 구성 요소 다운로드**|모든 필수 구성 요소 패키지가 지정한 위치에 복사되고 솔루션을 사용하여 설치됩니다.|

     [필수 구성 요소 대화 상자](../ide/reference/prerequisites-dialog-box.md)를 참조 하세요.

11. **업데이트** 단추를 선택 하 고, 각 최종 사용자의 VSTO 추가 기능 또는 사용자 지정에서 업데이트를 확인할 빈도를 지정한 다음 **확인** 단추를 선택 합니다.

    > [!NOTE]
    > CD 또는 이동식 드라이브를 사용 하 여 배포 하는 경우 **에는 업데이트 확인 안 함** 옵션 단추를 선택 합니다.

     업데이트를 게시 하는 방법에 대 한 자세한 내용은 [업데이트 게시](#Update)를 참조 하십시오.

12. **옵션 단추를** 선택 하 고 **옵션 대화 상자의 옵션을** 검토 한 다음 **확인** 단추를 선택 합니다.

13. **지금 게시** 단추를 선택 합니다.

     이 절차의 앞부분에서 지정한 게시 폴더에 다음과 같은 폴더 및 파일이 추가됩니다.

    - **응용 프로그램 파일** 폴더입니다.

    - 설치 프로그램

    - 최신 버전의 배포 매니페스트를 가리키는 배포 매니페스트

      **응용 프로그램 파일** 폴더에는 게시 하는 각 버전에 대 한 하위 폴더가 있습니다. 각 버전별 하위 폴더에는 다음 파일이 들어 있습니다.

    - 애플리케이션 매니페스트

    - 배포 매니페스트

    - 사용자 지정 어셈블리

      다음 그림에서는 Outlook VSTO 추가 기능용 게시 폴더의 구조를 보여 줍니다.

      ![폴더 구조 게시](../vsto/media/publishfolderstructure.png "게시 폴더 구조")

    > [!NOTE]
    > ClickOnce는 어셈블리에 .deploy 확장을 추가 하 여 안전 하지 않은 확장으로 인해 인터넷 정보 서비스 (IIS)의 보안 설치에서 파일을 차단 하지 않도록 *합니다.* 사용자가 솔루션을 설치할 때 ClickOnce는 *.deploy* 확장명을 제거 합니다.

14. 이 절차의 앞부분에서 지정한 설치 위치에 솔루션 파일을 복사합니다.

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a> 솔루션에 신뢰를 부여할 방법을 결정 합니다.
 사용자 컴퓨터에서 솔루션을 실행하려면 먼저 관리자가 신뢰를 부여하거나 사용자가 솔루션을 설치할 때 신뢰 프롬프트에 응답해야 합니다. 솔루션에 신뢰를 부여하려면 신뢰할 수 있고 확인된 게시자를 식별하는 인증서를 사용하여 매니페스트에 서명합니다. [응용 프로그램 및 배포 매니페스트에 서명 하 여 솔루션 신뢰](../vsto/granting-trust-to-office-solutions.md#Signing)를 참조 하세요.

 문서 수준 사용자 지정을 배포 하는 경우 문서를 사용자 컴퓨터의 폴더에 배치 하거나 SharePoint 사이트에서 문서를 사용할 수 있도록 하려면 Office에서 문서의 위치를 신뢰 하는지 확인 합니다. [문서에 신뢰 부여를](../vsto/granting-trust-to-documents.md)참조 하세요.

## <a name="help-users-install-the-solution"></a><a name="Helping"></a> 사용자가 솔루션을 설치 하도록 지원
 사용자는 설치 프로그램을 실행 하거나, 배포 매니페스트를 열거나, 문서 수준 사용자 지정 중 문서를 직접 열어 솔루션을 설치할 수 있습니다. 가장 좋은 방법은 사용자가 설치 프로그램을 사용하여 솔루션을 설치하는 것입니다. 다른 두 가지 방법으로 필수 구성 요소 소프트웨어가 설치 되어 있는지 확인할 수 없습니다. 사용자가 설치 위치에서 문서를 열려는 경우, Office 애플리케이션의 보안 센터에서 신뢰할 수 있는 위치 목록에 이 문서를 추가해야 합니다.

### <a name="opening-the-document-of-a-document-level-customization"></a>문서 수준 사용자 지정의 문서 열기
 사용자는 문서 수준 사용자 지정의 문서를 설치 위치에서 바로 열거나 문서를 자신의 로컬 컴퓨터로 복사한 다음 이 복사본을 열 수 있습니다.

 가장 좋은 방법은 여러 사용자가 동시에 동일한 복사본을 열려고 시도하지 않도록 사용자가 자신의 컴퓨터에서 문서의 복사본을 여는 것입니다. 이 방법을 적용하려면 사용자 컴퓨터에 문서를 복사하도록 설치 프로그램을 구성하면 됩니다. [최종 사용자의 컴퓨터에 솔루션 문서 저장 (문서 수준 사용자 지정에만 해당)을](#Put)참조 하세요.

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>IIS 웹 사이트에서 배포 매니페스트를 열어 솔루션을 설치 합니다.
 사용자는 웹에서 배포 매니페스트를 열어 Office 솔루션을 설치할 수 있습니다. 그러나 인터넷 정보 서비스 (IIS)의 보안 설치에서는 확장명이 *.vsto* 인 파일을 차단 합니다. 따라서 IIS를 사용하여 Office 솔루션을 배포하려면 먼저 IIS에서 MIME 형식을 정의해야 합니다.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>IIS 6.0에 .vsto MIME 형식을 추가하려면

1. Iis 6.0를 실행 하는 서버에서 **시작**  >  **모든 프로그램**  >  **관리 도구**  >   **인터넷 정보 서비스 (IIS) 관리자**를 선택 합니다.

2. 컴퓨터 이름, **웹 사이트** 폴더 또는 구성 중인 웹 사이트를 선택 합니다.

3. 메뉴 모음에서 **작업**  >  **속성**을 선택 합니다.

4. **HTTP 헤더** 탭에서 **MIME 형식** 단추를 선택 합니다.

5. **MIME 형식** 창에서 **새로 만들기** 단추를 선택 합니다.

6. **Mime 형식** 창에서 확장명으로 **.vsto** 을 입력 하 고 **응용 프로그램/x m s-vsto** 를 MIME 형식으로 입력 한 다음 새 설정을 적용 합니다.

    > [!NOTE]
    > 변경 내용이 적용되려면 World Wide Web Publishing 서비스를 다시 시작하거나 작업자 프로세스가 재생될 때까지 기다려야 합니다. 그런 다음 브라우저의 디스크 캐시를 플러시하고 *vsto* 파일을 다시 열어야 합니다.

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>IIS 7.0에 .vsto MIME 형식을 추가하려면

1. IIS 7.0를 실행 하는 서버에서 **시작**  >  **모든 프로그램**  >  **보조 프로그램**을 선택 합니다.

2. **명령 프롬프트**의 바로 가기 메뉴를 열고 **관리자 권한으로 실행을 선택 합니다.**

3. **열기** 상자에 다음 경로를 입력 하 고 **확인** 단추를 선택 합니다.

    ```cmd
    %windir%\system32\inetsrv
    ```

4. 다음 명령을 입력한 다음 새로운 설정을 적용합니다.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > 변경 내용이 적용되려면 World Wide Web Publishing 서비스를 다시 시작하거나 작업자 프로세스가 재생될 때까지 기다려야 합니다. 그런 다음 브라우저의 디스크 캐시를 플러시하고 *vsto* 파일을 다시 열어야 합니다.

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a> 최종 사용자의 컴퓨터에 솔루션 문서 저장 (문서 수준 사용자 지정에만 해당)
 배포 후 작업을 만들어 솔루션의 문서를 최종 사용자의 컴퓨터에 복사할 수 있습니다. 이렇게 하면 사용자가 솔루션을 설치한 후 설치 위치에서 해당 컴퓨터에 문서를 수동으로 복사할 필요가 없습니다. 배포 후 작업을 정의 하 고, 솔루션을 빌드 및 게시 하 고, 응용 프로그램 매니페스트를 수정 하 고, 응용 프로그램 및 배포 매니페스트에 다시 서명 하는 클래스를 만들어야 합니다.

 다음 절차에서는 프로젝트 이름이 (가) **통합 문서** 이 고, 컴퓨터의 **c:\publish** 라는 생성 된 폴더에 솔루션을 게시 한다고 가정 합니다.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>배포 후 작업을 정의하는 클래스를 만듭니다.

1. 메뉴 모음에서 **파일**  >  **Add**  >  **새 프로젝트**추가를 선택 합니다.

2. **새 프로젝트 추가** 대화 상자의 **설치 된 템플릿** 창에서 **Windows** 폴더를 선택 합니다.

3. **템플릿** 창에서 **클래스 라이브러리** 템플릿을 선택 합니다.

4. **이름** 필드에 **FileCopyPDA**를 입력 하 고 **확인** 단추를 선택 합니다.

5. **솔루션 탐색기**에서 **FileCopyPDA** 프로젝트를 선택 합니다.

6. 메뉴 모음에서 **프로젝트** > **참조 추가**를 선택합니다.

7. **.Net** 탭에서 및에 대 한 참조를 추가 `Microsoft.VisualStudio.Tools.Applications.Runtime` `Microsoft.VisualStudio.Tools.Applications.ServerDocument` 합니다.

8. 클래스 이름을 `FileCopyPDA`로 바꾼 다음 파일의 내용을 이 코드로 바꿉니다. 이 코드는 다음 작업을 수행합니다.

   - 사용자의 바탕 화면에 문서를 복사합니다.

   - _AssemblyLocation 속성을 상대 경로에서 배포 매니페스트의 정규화 된 경로로 변경 합니다.

   - 사용자가 솔루션을 제거한 경우 파일을 삭제합니다.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>솔루션을 빌드하고 게시합니다.

1. **솔루션 탐색기**에서 **FileCopyPDA** 프로젝트에 대 한 바로 가기 메뉴를 열고 **빌드**를 선택 합니다.

2. **Excel 통합 문서** 프로젝트에 대 한 바로 가기 메뉴를 열고 **빌드**를 선택 합니다.

3. **Excel 통합 문서** 프로젝트에 대 한 바로 가기 메뉴를 열고 **참조 추가**를 선택 합니다.

4. **참조 추가** 대화 상자에서 **프로젝트** 탭을 선택 하 고 **FileCopyPDA**를 선택한 다음 **확인** 단추를 선택 합니다.

5. **솔루션 탐색기**에서 **excel 통합 문서** 프로젝트를 선택 합니다.

6. 메뉴 모음에서 **프로젝트**  >  **새 폴더**를 선택 합니다.

7. **데이터**를 입력 한 다음 **enter** 키를 선택 합니다.

8. **솔루션 탐색기**에서 **데이터** 폴더를 선택 합니다.

9. 메뉴 모음에서 **프로젝트**  >  **기존 항목 추가**를 선택 합니다.

10. **기존 항목 추가** 대화 상자에서 **excel 통합 문서** 프로젝트의 출력 디렉터리로 이동 하 고 **ExcelWorkbook.xlsx** 파일을 선택한 다음 **추가** 단추를 선택 합니다.

11. **솔루션 탐색기** 에서 **ExcelWorkbook.xlsx** 파일을 선택 합니다.

12. **속성** 창에서 **빌드 작업** 속성을 **내용** 으로 변경 하 고 **출력 디렉터리로 복사** 속성을 변경 된 **내용만 복사**로 변경 합니다.

     이러한 단계를 완료 하면 프로젝트는 다음 그림과 유사 하 게 표시 됩니다.

     ![배포 후 작업의 프로젝트 구조입니다.](../vsto/media/vsto-postdeployment.png "배포 후 작업의 프로젝트 구조입니다.")

13. **Excel 통합 문서** 프로젝트를 게시 합니다.

### <a name="modify-the-application-manifest"></a>애플리케이션 매니페스트 수정

1. **파일 탐색기**를 사용 하 여 솔루션 디렉터리 **c:\publish**를 엽니다.

2. **응용 프로그램 파일** 폴더를 연 다음 솔루션의 최근 게시 된 버전에 해당 하는 폴더를 엽니다.

3. 메모장 등의 텍스트 편집기에서 **ExcelWorkbook.dll 매니페스트** 파일을 엽니다.

4. `</vstav3:update>` 요소 뒤에 다음 코드를 추가합니다. 요소의 클래스 특성에는 `<vstav3:entryPoint>` 다음 구문을 사용 합니다. *NamespaceName*. 다음 예제에서는 네임스페이스 및 클래스 이름이 같기 때문에 결과 진입점 이름은 `FileCopyPDA.FileCopyPDA`입니다.

    ```xml
    <vstav3:postActions>
      <vstav3:postAction>
        <vstav3:entryPoint
          class="FileCopyPDA.FileCopyPDA">
          <assemblyIdentity
            name="FileCopyPDA"
            version="1.0.0.0"
            language="neutral"
            processorArchitecture="msil" />
        </vstav3:entryPoint>
        <vstav3:postActionData>
        </vstav3:postActionData>
      </vstav3:postAction>
    </vstav3:postActions>
    ```

### <a name="re-sign-the-application-and-deployment-manifests"></a>애플리케이션 및 배포 매니페스트 다시 서명

1. **%USERPROFILE%\Documents\Visual Studio 2013 \ projects\s\wors\s\\Application 통합 문서** 폴더에서 **ExcelWorkbook_TemporaryKey .pfx** 인증서 파일을 복사 하 여 *worfolder* **Files\ExcelWorkbook** \_ _MostRecentPublishedVersion_ 폴더에 붙여넣습니다.

2. Visual Studio 명령 프롬프트를 열고 디렉터리를 **c:\publish\Application Files\ExcelWorkbook** \_ _MostRecentPublishedVersion_ 폴더로 변경 합니다 (예: **c:\publish\Application files\ ExcelWorkbook_1_0_0_4**).

3. 다음 명령을 실행하여 수정된 애플리케이션 매니페스트에 서명합니다.

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     "ExcelWorkbook.dll.manifest에 서명했습니다"라는 메시지가 나타납니다.

4. **C:\publish** 폴더로 변경한 후 다음 명령을 실행 하 여 배포 매니페스트를 업데이트 하 고 서명 합니다.

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > 이전 예제에서 MostRecentVersionNumber를 솔루션의 가장 최근에 게시 된 버전 (예: **1_0_0_4**)의 버전 번호로 바꿉니다.

     "ExcelWorkbook.vsto에 서명했습니다."라는 메시지가 나타납니다.

5. **C:\publish\Application Files\ExcelWorkbook**MostRecentVersionNumber 디렉터리에 *파일을 복사 합니다* \_ _MostRecentVersionNumber_ .

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a> SharePoint를 실행 하는 서버에 솔루션 문서 저장 (문서 수준 사용자 지정에만 해당)
 SharePoint를 사용하여 최종 사용자에게 문서 수준 사용자 지정을 게시할 수 있습니다. 사용자가 SharePoint 사이트에서 문서를 열면 런타임에 자동으로 공유 네트워크 폴더의 솔루션을 사용자의 로컬 컴퓨터에 설치합니다. 솔루션이 로컬로 설치된 후, 문서가 바탕 화면과 같은 다른 위치에 복사되는 경우에도 사용자 지정은 계속 작동합니다.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>SharePoint를 실행하는 서버에 문서를 저장하려면

1. SharePoint 사이트의 문서 라이브러리에 솔루션 문서를 추가합니다.

2. 다음 방법 중 하나에 해당하는 단계를 수행합니다.

    - Office 구성 도구를 사용하여 모든 사용자 컴퓨터에 있는 Word 또는 Excel의 보안 센터에 SharePoint 실행 서버를 추가합니다.

         [Office 2010의 보안 정책 및 설정](/previous-versions/office/office-2010/cc178946(v=office.14))을 참조 하세요.

    - 각 사용자는 다음 단계를 수행해야 합니다.

        1. 로컬 컴퓨터에서 Word 또는 Excel을 열고 **파일** 탭을 선택한 다음 **옵션** 단추를 선택 합니다.

        2. **보안 센터** 대화 상자에서 **신뢰할 수 있는 위치** 단추를 선택 합니다.

        3. **네트워크에서 신뢰할 수 있는 위치 허용 (권장 하지 않음)** 확인란을 선택 하 고 **새 위치 추가** 단추를 선택 합니다.

        4. **경로** 상자에 업로드 한 문서를 포함 하는 SharePoint 문서 라이브러리의 URL (예:)을 입력 *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName* 합니다.

             기본 웹 페이지의 이름을 추가 하지 마세요 (예: default.aspx *또는* *AllItems*).

        5. **이 위치의 하위 폴더도 신뢰할 수 있음** 확인란을 선택 하 고 **확인** 단추를 선택 합니다.

             사용자가 SharePoint 사이트에서 문서를 열면 이 문서가 열리고 사용자 지정이 설치됩니다. 사용자는 바탕 화면에 이 문서를 복사할 수 있습니다. 문서의 속성에서 문서의 네트워크 위치를 가리키므로 사용자 지정은 계속 실행됩니다.

## <a name="create-a-custom-installer"></a><a name="Custom"></a> 사용자 지정 설치 관리자 만들기
 솔루션을 게시할 때 생성 된 설치 프로그램을 사용 하는 대신 Office 솔루션에 대 한 사용자 지정 설치 관리자를 만들 수 있습니다. 예를 들어, 로그인 스크립트를 사용 하 여 설치를 시작 하거나, 배치 파일을 사용 하 여 사용자 개입 없이 솔루션을 설치할 수 있습니다. 이러한 시나리오는 최종 사용자의 컴퓨터에 필수 구성 요소가 이미 설치된 경우에 가장 적합합니다.

 사용자 지정 설치 프로세스의 일부로 기본적으로 다음 위치에 설치 되는 Office 솔루션용 설치 관리자 도구 (*VSTOInstaller.exe*)를 호출 합니다.

 *%commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 도구가 해당 위치에 없으면 **HKEY_LOCAL_MACHINE \Software\microsoft\vsto runtime Setup\v4\InstallerPath** 또는 **HKEY_LOCAL_MACHINE \software\wow6432node\microsoft\vsto runtime Setup\v4\InstallerPath** 레지스트리 키를 사용 하 여 해당 도구에 대 한 경로를 찾을 수 있습니다.

 *VSTOinstaller.exe*에서 다음 매개 변수를 사용할 수 있습니다.

| 매개 변수 | 정의 |
|------------------| - |
| /Install 또는 /I | 솔루션을 설치합니다. 이 옵션 뒤에는 배포 매니페스트의 경로가 와야 합니다. 로컬 컴퓨터, UNC(Universal Naming Convention) 파일 공유에 대한 경로를 지정할 수 있습니다. 로컬 경로 (*C:\foldername\publishfolder*), 상대 경로 (*게시 \\ *) 또는 정규화 된 위치 (* \\ \ServerName\FolderName* 또는 http://<em>ServerName/FolderName</em>)를 지정할 수 있습니다. |
| /Uninstall 또는 /U | 솔루션을 제거합니다. 이 옵션 뒤에는 배포 매니페스트의 경로가 와야 합니다. 경로를 로컬 컴퓨터의 UNC 파일 공유로 지정할 수 있습니다. 로컬 경로 (*C:\foldername\publishfolder*), 상대 경로 (*게시 \\ *) 또는 정규화 된 위치 (* \\ \ServerName\FolderName* 또는 http://<em>ServerName/FolderName</em>)를 지정할 수 있습니다. |
| /Silent 또는 /S | 입력에 대한 메시지나 그 밖의 메시지를 사용자에게 표시하지 않고 설치 또는 제거합니다. 신뢰 프롬프트가 필요 하면 사용자 지정이 설치 되거나 업데이트 되지 않습니다. |
| /Help 또는 /? | 도움말 정보를 표시합니다. |

 *VSTOinstaller.exe*를 실행 하면 다음 오류 코드가 나타날 수 있습니다.

|오류 코드|정의|
|----------------|----------------|
|0|솔루션이 성공적으로 설치되었거나 제거되었습니다. 또는 VSTOInstaller 도움말이 표시되었습니다.|
|-100|하나 이상의 명령줄 옵션이 잘못 되었거나 두 번 이상 설정 되었습니다. 자세한 내용을 보려면 "vstoinstaller/?"를 입력 하십시오. 또는 [ClickOnce Office 솔루션에 대 한 사용자 지정 설치 관리자 만들기](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)를 참조 하세요.|
|-101|하나 이상의 명령줄 옵션이 잘못 되었습니다. 자세한 내용을 보려면 "vstoinstaller /?"를 입력하십시오.|
|-200|배포 매니페스트 URI가 잘못 되었습니다. 자세한 내용을 보려면 "vstoinstaller /?"를 입력하십시오.|
|-201|배포 매니페스트가 잘못 되었으므로 솔루션을 설치할 수 없습니다. [Office 솔루션에 대 한 배포 매니페스트를](../vsto/deployment-manifests-for-office-solutions.md)참조 하세요.|
|-202|응용 프로그램 매니페스트의 Visual Studio Tools for Office 섹션이 잘못 되었으므로 솔루션을 설치할 수 없습니다. [Office 솔루션의 응용 프로그램 매니페스트를](../vsto/application-manifests-for-office-solutions.md)참조 하세요.|
|-203|다운로드 오류가 발생 하 여 솔루션을 설치할 수 없습니다. 배포 매니페스트의 URI 또는 네트워크 파일 위치를 확인한 다음 다시 시도하세요.|
|-300|보안 예외가 발생 하 여 솔루션을 설치할 수 없습니다. [Office 솔루션 보안](../vsto/securing-office-solutions.md)을 참조 하세요.|
|-400|솔루션을 설치할 수 없습니다.|
|-401|솔루션을 제거할 수 없습니다.|
|-500|솔루션을 설치 또는 제거할 수 없거나 배포 매니페스트를 다운로드할 수 없어 작업이 취소되었습니다.|

## <a name="publish-an-update"></a><a name="Update"></a> 업데이트 게시
 솔루션을 업데이트 하려면 **프로젝트 디자이너나** **게시 마법사**를 사용 하 여 솔루션을 다시 게시 한 다음 업데이트 된 솔루션을 설치 위치에 복사 합니다. 설치 위치에 파일을 복사하면 이전 파일을 덮어쓰게 됩니다.

 다음 번에 솔루션에서 업데이트를 확인 하면 새 버전이 자동으로 검색 되 고 로드 됩니다.

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a> 솔루션의 설치 위치 변경
 솔루션이 게시된 후 설치 경로를 추가하거나 변경할 수 있습니다. 다음 이유 중 하나 이상으로 인해 설치 경로를 변경하려 할 수 있습니다.

- 설치 경로가 알려지기 전에 설치 프로그램을 컴파일한 경우

- 솔루션 파일이 다른 위치에 복사된 경우

- 설치 파일이 호스팅된 서버에 새 이름 또는 위치가 있는 경우

  솔루션의 설치 경로를 변경하려면 설치 프로그램을 업데이트한 다음 사용자가 이를 실행해야 합니다. 문서 수준 사용자 지정의 경우, 사용자가 문서의 속성이 새 위치를 가리키도록 업데이트해야 합니다.

> [!NOTE]
> 사용자에 게 문서 속성을 업데이트 하 라는 메시지를 표시 하지 않으려면 설치 위치에서 업데이트 된 문서를 가져오도록 사용자에 게 요청할 수 있습니다.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>설치 프로그램에서 설치 경로를 변경하려면

1. **명령 프롬프트** 창을 열고 디렉터리를 설치 폴더로 변경 합니다.

2. 설치 프로그램을 실행하고 새 설치 경로를 문자열로 받아들이는 `/url` 매개 변수를 포함시킵니다.

    다음 예제에서는 Fabrikam 웹 사이트에 있는 위치로 설치 경로를 변경하는 방법을 보여 주지만, 해당 URL을 원하는 경로로 바꿀 수 있습니다.

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > 메시지가 표시되어 실행 파일의 시그니처가 무효가 되었음을 알리는 경우, 솔루션 서명에 사용된 인증서는 더 이상 유효하지 않으며 게시자는 알 수 없게 됩니다. 그 결과 사용자는 솔루션의 소스를 신뢰함을 확인한 뒤에야 이를 설치할 수 있게 됩니다.

   > [!NOTE]
   > 현재 URL 값을 표시하려면 `setup.exe /url`을 실행하십시오.

   문서 수준 사용자 지정의 경우 사용자가 문서를 열고 _AssemblyLocation 속성을 업데이트 해야 합니다. 다음 단계에서는 사용자가 이 작업을 수행하는 방법을 설명합니다.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>문서에서 _AssemblyLocation 속성을 업데이트하려면

1. 다음 그림에 표시 된 **파일** 탭에서 **정보**를 선택 합니다.

     ![Excel의 정보 탭](../vsto/media/vsto-infotab.png "Excel의 정보 탭")

2. **속성** 목록에서 다음 그림에 표시 된 **고급 속성**을 선택 합니다.

     ![Excel의 고급 속성입니다.](../vsto/media/vsto-advanceddocumentproperties.png "Excel의 고급 속성입니다.")

3. 다음 그림과 같이 **속성** 목록의 **사용자 지정** 탭에서 _AssemblyLocation를 선택 합니다.

     ![AssemblyLocation 속성입니다.](../vsto/media/vsto-assemblylocationproperty.png "AssemblyLocation 속성입니다.")

     **값** 상자에는 배포 매니페스트 식별자가 포함 됩니다.

4. 식별자 앞에 문서에 대 한 정규화 *된 경로를*입력 합니다 | *Identifier* (예: *File://ServerName/FolderName/FileName|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*).

     이 식별자의 형식을 지정 하는 방법에 대 한 자세한 내용은 [사용자 지정 문서 속성 개요](../vsto/custom-document-properties-overview.md)를 참조 하세요.

5. **확인** 단추를 선택 하 고 문서를 저장 한 후 닫습니다.

6. /url 매개 변수를 사용하지 않고 설치 프로그램을 실행하여 지정한 위치에 솔루션을 설치합니다.

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a> 이전 버전으로 솔루션 롤백
 솔루션을 롤백하면 사용자의 해당 솔루션이 이전 버전으로 돌아갑니다.

#### <a name="to-roll-back-a-solution"></a>솔루션을 롤백하려면

1. 솔루션의 설치 위치를 엽니다.

2. 최상위 게시 폴더에서 배포 매니페스트 ( *.vsto* 파일)를 삭제 합니다.

3. 롤백할 버전의 하위 폴더를 찾습니다.

4. 해당 하위 폴더의 배포 매니페스트를 최상위 게시 폴더에 복사합니다.

     예를 들어 **outlookaddin1.dll** 이라는 솔루션을 버전 1.0.0.1에서 버전 1.0.0.0으로 롤백하려면 **OutlookAddIn1_1_0_0_0** 폴더에서 **outlookaddin1.dll** 파일을 복사 합니다. 최상위 게시 폴더에 파일을 붙여넣어 이미 있는 **OutlookAddIn1_1_0_0_1** 에 대 한 버전별 배포 매니페스트를 덮어씁니다.

     다음 그림에서는 이 예제의 게시 폴더 구조를 보여 줍니다.

     ![폴더 구조 게시](../vsto/media/publishfolderstructure.png "게시 폴더 구조")

     다음에 사용자가 애플리케이션 또는 사용자 지정 문서를 열면 배포 매니페스트 변경 사항이 검색됩니다. 이전 버전의 Office 솔루션은 ClickOnce 캐시에서 실행됩니다.

> [!NOTE]
> 로컬 데이터는 이전 버전의 솔루션 하나에 대해서만 저장됩니다. 두 버전을 롤백하는 경우 로컬 데이터가 보존 되지 않습니다. 로컬 데이터에 대 한 자세한 내용은 [ClickOnce 응용 프로그램의 로컬 및 원격 데이터 액세스](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보

- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
- [Office 솔루션 게시](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [방법: ClickOnce를 사용 하 여 Office 솔루션 게시](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [방법: ClickOnce Office 솔루션 설치](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)
- [방법: ClickOnce를 사용 하 여 SharePoint 서버에 문서 수준 Office 솔루션 게시](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)
- [ClickOnce office 솔루션에 대 한 사용자 지정 설치 관리자 만들기](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)