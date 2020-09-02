---
title: Visual Studio에서 SharePoint 도구에 대 한 확장 디버깅 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e170a5ed703a9bf5aae2e73126de52ecf88e8084
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64785343"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Visual Studio의 SharePoint 도구에 대 한 디버그 확장
  Visual Studio의 실험적 인스턴스나 일반 인스턴스에서 SharePoint 도구 확장을 디버그할 수 있습니다. 확장의 동작에 대 한 문제를 해결 해야 하는 경우 추가 오류 정보를 표시 하 고 Visual Studio에서 SharePoint 명령을 실행 하는 방법을 구성 하는 레지스트리 값을 수정할 수도 있습니다.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Visual Studio의 실험적 인스턴스에서 확장 디버그
 Visual Studio 개발 환경을 테스트 되지 않은 확장의 우발적 손상 으로부터 보호 하기 위해 Visual Studio SDK는 확장을 설치 하 고 테스트 하는 데 사용할 수 있는 *실험적 인스턴스*라는 대체 visual studio 인스턴스를 제공 합니다. Visual Studio의 일반 인스턴스를 사용 하 여 새 확장을 개발 하지만 실험적 인스턴스에서 디버그 하 고 실행 합니다. 자세한 내용은 [실험적 인스턴스](../extensibility/the-experimental-instance.md)를 참조 하세요.

 VSIX 프로젝트를 사용 하 여 확장을 배포 하 고 VSIX 프로젝트가 솔루션의 시작 프로젝트인 경우 솔루션을 디버그할 때 Visual Studio에서 자동으로 실험적 인스턴스에 확장을 설치 하 고 실행 합니다. 시작 프로젝트는 여러 프로젝트가 포함 된 솔루션을 디버그할 때 시작 되는 프로젝트입니다. VSIX 프로젝트를 사용 하 여 확장을 배포 하는 방법에 대 한 자세한 내용은 [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)를 참조 하세요.

 Visual Studio의 실험적 인스턴스에서 다양 한 형식의 확장을 디버그 하는 방법을 보여 주는 예제는 다음 연습을 참조 하세요.

- [연습: SharePoint 프로젝트 항목 형식 확장](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

- [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

- [연습: SharePoint 프로젝트에 대 한 사용자 지정 배포 단계 만들기](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

- [연습: 서버 탐색기 확장 하 여 웹 파트 표시](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

- [연습: 서버 탐색기 확장에서 SharePoint 클라이언트 개체 모델 호출](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Visual Studio의 일반 인스턴스에서 확장 디버그
 Visual Studio의 일반 인스턴스에서 확장 프로젝트를 디버깅 하려면 먼저 일반 인스턴스에 확장을 설치 합니다. 그런 다음 디버거를 두 번째 Visual Studio 프로세스에 연결 합니다. 작업이 완료 되 면 개발 컴퓨터에서 더 이상 로드 되지 않도록 확장을 제거할 수 있습니다.

#### <a name="to-install-the-extension"></a>확장을 설치하려면

1. Visual Studio의 모든 인스턴스를 닫습니다.

2. 확장 프로젝트에 대 한 빌드 출력 폴더에서 .vsix 파일을 두 번 클릭 하거나 바로 가기 메뉴를 열고 **열기**를 선택 하 여 엽니다 *.*

3. **Visual Studio 확장 설치 관리자** 대화 상자에서 확장을 설치할 visual studio 버전을 선택한 후 **설치** 단추를 선택 합니다.

     Visual Studio 는%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions \\ *author 이름* \\ *확장 이름* \\ *버전*에 확장 파일을 설치 합니다. 이 경로의 마지막 3 개 폴더는 `Author` `Name` `Version` 확장에 대 한 *source.extension.vsixmanifest* 파일의, 및 요소에서 생성 됩니다.

4. Visual Studio에서 확장을 설치한 후 **닫기** 단추를 선택 합니다.

#### <a name="to-debug-the-extension"></a>확장을 디버깅 하려면

1. 관리자 권한으로 Visual Studio를 열고 확장 프로젝트를 엽니다. 다음 단계에서는 Visual Studio의이 인스턴스를 *첫 번째 인스턴스로*참조 합니다.

2. 관리자 권한으로 Visual Studio의 다른 인스턴스를 시작 합니다. 다음 단계에서는 Visual Studio의이 인스턴스를 *두 번째 인스턴스로*참조 합니다.

3. Visual Studio의 첫 번째 인스턴스로 전환 합니다.

4. 메뉴 모음에서 **디버그**, **프로세스에 연결**을 선택 합니다.

5. **사용 가능한 프로세스** 목록에서 *devenv.exe*을 선택 합니다. 이 항목은 Visual Studio의 두 번째 인스턴스를 참조 합니다. 프로젝트 확장을 디버깅 하려는 인스턴스입니다.

6. **연결** 단추를 선택 합니다.

     Visual Studio는 디버그 모드에서 확장 프로젝트를 실행 합니다.

7. Visual Studio의 두 번째 인스턴스로 전환 합니다.

8. 확장을 로드 하는 새 SharePoint 프로젝트를 만듭니다. 예를 들어 목록 정의 프로젝트 항목에 대 한 확장을 디버그 하는 경우 **목록 정의** 프로젝트를 만듭니다.

9. 확장 코드를 테스트 하는 데 필요한 단계를 수행 합니다.

10. 확장 디버깅을 마쳤으면 Visual Studio의 두 번째 인스턴스를 닫습니다.

#### <a name="to-remove-the-extension"></a>확장을 제거 하려면

1. Visual Studio의 메뉴 모음에서 **도구**, **확장 및 업데이트**를 선택 합니다.

     **확장명 및 업데이트** 대화 상자가 열립니다.

2. 확장 목록에서 확장의 이름을 선택한 다음 **제거** 단추를 선택 합니다.

3. 표시 되는 대화 상자에서 **예** 단추를 선택 하 여 확장을 제거할 것임을 확인 합니다.

4. **지금 다시 시작** 단추를 선택 하 여 제거를 완료 합니다.

## <a name="debug-sharepoint-commands"></a>SharePoint 명령 디버그
 SharePoint 도구 확장의 일부인 SharePoint 명령을 디버깅 하려면 디버거를 *vssphost4.exe* 프로세스에 연결 해야 합니다. 이는 SharePoint 명령을 실행 하는 64 비트 호스트 프로세스입니다. SharePoint 명령 및 *vssphost4.exe*에 대 한 자세한 내용은 [Sharepoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)을 참조 하세요.

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>디버거를 vssphost4.exe 프로세스에 연결 하려면

1. Visual Studio의 실험적 인스턴스나 위의 지침에 따라 Visual Studio의 일반 인스턴스에서 확장 디버깅을 시작 합니다.

2. 디버거를 실행 하는 Visual Studio 인스턴스의 메뉴 모음에서 **디버그**, **프로세스에 연결**을 선택 합니다.

3. **사용 가능한 프로세스** 목록에서 *vssphost.exe*을 선택 합니다.

    > [!NOTE]
    > vssphost.exe 목록에 표시 되지 않으면 확장을 실행 하는 Visual Studio 인스턴스에서 *vssphost4.exe* 프로세스를 시작 해야 합니다. 일반적으로 Visual Studio가 개발 컴퓨터의 SharePoint 사이트에 연결 하는 작업을 수행 하 여이 작업을 수행 합니다. 예를 들어 Visual Studio는 **서버 탐색기** 창의 **SharePoint 연결** 노드 아래에서 사이트 연결 노드 (사이트 URL을 표시 하는 노드)를 확장 하거나 **인스턴스** 또는 **이벤트 받는 사람** 항목 등의 특정 sharepoint 프로젝트 항목을 sharepoint 프로젝트에 추가할 때 *vssphost4.exe* 를 시작 합니다.

4. **연결** 단추를 선택 합니다.

5. 디버깅 중인 Visual Studio 인스턴스에서 명령을 실행 하는 데 필요한 단계를 수행 합니다.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>SharePoint 도구 확장을 디버그 하는 데 도움이 되도록 레지스트리 값 수정
 Visual Studio에서 SharePoint 도구의 확장을 디버깅할 때 확장 문제를 해결 하는 데 도움이 되도록 레지스트리의 값을 수정할 수 있습니다. 값은 **HKEY_CURRENT_USER \software\microsoft\visualstudio\11.0\sharepointtools** 키 아래에 있습니다. 이러한 값은 기본적으로 존재 하지 않습니다.

 SharePoint 도구의 확장 문제를 해결 하는 데 도움이 되도록 EnableDiagnostics 값을 만들고 설정할 수 있습니다. 다음 표에서는이 값에 대해 설명 합니다.

|값|설명|
|-----------|-----------------|
|EnableDiagnostics|진단 메시지를 **출력** 창에 표시할지 여부를 지정 하는 REG_DWORD입니다.<br /><br /> 진단 메시지를 표시 하려면이 값을 1로 설정 합니다. 메시지 표시를 중지 하려면이 값을 0으로 설정 하거나이 값을 삭제 합니다.<br /><br /> SharePoint 도구 확장에서 **출력** 창에 메시지를 쓰려면 sharepoint 프로젝트 서비스를 사용 합니다. 자세한 내용은 [SharePoint 프로젝트 서비스 사용](../sharepoint/using-the-sharepoint-project-service.md)을 참조 하세요.|

 확장에 SharePoint 명령이 포함 된 경우 명령 문제를 해결 하는 데 도움이 되도록 추가 값을 만들고 설정할 수 있습니다. 다음 표에서는 이러한 값에 대해 설명합니다.

|값|설명|
|-----------|-----------------|
|AttachDebuggerToHostProcess|디버거를 시작 하는 즉시 *vssphost4.exe* 에 연결할 수 있는 대화 상자를 표시할지 여부를 지정 하는 REG_DWORD입니다. 이 기능은 디버그 하려는 명령이 시작 된 직후에 vssphost.exe에서 실행 되 고 명령이 실행 되기 전에 디버거를 수동으로 연결할 시간이 충분 하지 않은 경우에 유용 합니다. 대화 상자를 표시 하려면 *vssphost4.exe* <xref:System.Diagnostics.Debugger.Break%2A> 시작 될 때 메서드를 호출 합니다.<br /><br /> 이 동작을 사용 하도록 설정 하려면이 값을 1로 설정 합니다. 이 동작을 해제 하려면이 값을 0으로 설정 하거나이 값을 삭제 합니다.<br /><br /> 이 값을 1로 설정 하는 경우 Visual Studio가 성공적으로 시작 되었음을 알리기 위해 *vssphost4.exe* 하기 전에 디버거를 연결할 시간이 충분 하도록 HostProcessStartupTimeout 값을 늘릴 수도 있습니다.|
|ChannelOperationTimeout|Visual Studio에서 SharePoint 명령이 실행 될 때까지 대기 하는 시간 (초)을 지정 하는 REG_DWORD입니다. 명령이 시간 내에 실행 되지 않으면 <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> 이 throw 됩니다.<br /><br /> 기본값은 120초입니다.|
|HostProcessStartupTimeout|Visual Studio에서 *vssphost4.exe* 성공적으로 시작 되었음을 알리기 위해 대기 하는 시간 (초)을 지정 하는 REG_DWORD입니다. *vssphost4.exe* 가 성공적으로 시작 된 시간에 신호를 보내지 않으면 <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> 이 throw 됩니다.<br /><br /> 기본값은 60초입니다.|
|MaxReceivedMessageSize|Visual Studio와 *vssphost4.exe*간에 전달 되는 WCF 메시지의 최대 허용 크기 (바이트)를 지정 하는 REG_DWORD입니다.<br /><br /> 기본값은 1048576 바이트 (1mb)입니다.|
|MaxStringContentLength|Visual Studio와 *vssphost4.exe*간에 전달 되는 문자열의 최대 허용 크기 (바이트)를 지정 하는 REG_DWORD입니다.<br /><br /> 기본값은 1048576 바이트 (1mb)입니다.|

## <a name="see-also"></a>추가 정보

- [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
