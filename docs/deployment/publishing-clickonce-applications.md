---
title: ClickOnce 응용 프로그램 게시 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Options
- Microsoft.VisualStudio.Publish.ClickOnceProvider.PublishWizard.Help
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- ClickOnce applications, publishing
- applications [Visual Studio], ClickOnce deployment
- deploying applications [ClickOnce], publishing ClickOnce applications
ms.assetid: eb6dfe79-f54c-4331-8e36-073688e70973
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41cd62e8831ac4edd5b37337c1e72dd0b2e662e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536294"
---
# <a name="publish-clickonce-applications"></a>ClickOnce 애플리케이션 게시
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션을 처음으로 게시할 때는 게시 마법사를 사용하여 게시 속성을 설정할 수 있습니다. 마법사에서는 일부 속성만 사용 가능하며 기타 모든 설정은 기본값으로 설정됩니다.

 이후 게시 속성 변경은 **프로젝트 디자이너**의 **게시** 페이지에서 수행합니다.

## <a name="publish-wizard"></a>게시 마법사
 게시 마법사를 사용하여 애플리케이션 게시를 위한 기본 설정을 지정할 수 있습니다. 여기에는 다음과 같은 게시 속성이 포함됩니다.

- 게시 폴더 위치 - Visual Studio에서 파일을 복사하는 위치(로컬 컴퓨터, 네트워크 파일 공유, FTP 서버 또는 웹 사이트)

- 설치 폴더 위치 - 최종 사용자가 설치하는 위치(네트워크 파일 공유, FTP 서버, 웹 사이트, CD/DVD)

- 온라인 또는 오프라인 사용 가능 여부 - 최종 사용자가 네트워크에 연결하지 않고 애플리케이션에 액세스할 수 있는지 여부

- 업데이트 빈도 - 애플리케이션에서 새 업데이트를 확인하는 빈도

  자세한 내용은 [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)를 참조 하세요.

## <a name="publish-page"></a>게시 페이지
 **프로젝트 디자이너** 의 **게시** 페이지를 통해 ClickOnce 배포를 위한 속성을 구성합니다. 다음 표에 관련 항목이 나와 있습니다.

|제목|설명|
|-----------|-----------------|
|[방법: Visual Studio의 파일 복사 위치 지정](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Visual Studio에서 애플리케이션 파일 및 매니페스트를 배치하는 위치를 설정하는 방법을 설명합니다.|
|[방법: 최종 사용자가 설치하는 원본 위치 지정](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|사용자가 애플리케이션을 다운로드하고 설치할 수 있는 위치를 설정하는 방법을 설명합니다.|
|[방법: ClickOnce 오프라인 또는 온라인 설치 모드 지정](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|애플리케이션을 오프라인으로 제공할지 아니면 온라인으로 제공할지를 설정하는 방법을 설명합니다.|
|[방법: ClickOnce 게시 버전 설정](../deployment/how-to-set-the-clickonce-publish-version.md)|게시하는 애플리케이션을 업데이트로 간주할지 여부를 결정하는 ClickOnce **게시 버전** 속성을 설정하는 방법을 설명합니다.|
|[방법: ClickOnce 게시 버전 자동 증가](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|애플리케이션을 게시할 때마다 **PublishVersion**의 수정 번호를 자동으로 증분하는 방법을 설명합니다.|

 자세한 내용은 [프로젝트 디자이너, 게시 페이지](../ide/reference/publish-page-project-designer.md) 를 참조 하세요.

### <a name="application-files-dialog-box"></a>애플리케이션 파일 대화 상자
 이 대화 상자에서는 프로젝트의 파일이 게시, 동작 다운로드 및 업데이트용으로 분류되는 방법을 지정할 수 있습니다. 이 대화 상자에 포함된 표에는 기본적으로 제외되지 않거나 다운로드 그룹이 있는 프로젝트 파일이 나열됩니다.

 파일을 제외 하 고, 파일을 데이터 파일 또는 필수 구성 요소로 표시 하 고, Visual Studio UI에서 조건부 설치용 파일 그룹을 만들려면 [방법: ClickOnce에서 게시할 파일 지정](../deployment/how-to-specify-which-files-are-published-by-clickonce.md)을 참조 하세요. Mage.exe를 사용하여 데이터 파일을 표시할 수도 있습니다. 자세한 내용은 [방법: ClickOnce 응용 프로그램에 데이터 파일 포함](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)을 참조 하세요.

### <a name="prerequisites-dialog-box"></a>필수 조건 대화 상자
 이 대화 상자에서는 설치되는 필수 구성 요소 및 해당 설치 방법을 지정합니다. 자세한 내용은 [방법: ClickOnce 응용 프로그램을 사용 하 여 필수 구성 요소 설치](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) 및 [필수 구성 요소 대화 상자](../ide/reference/prerequisites-dialog-box.md)를 참조 하세요.

### <a name="application-updates-dialog-box"></a>애플리케이션 업데이트 대화 상자
 이 대화 상자에서는 설치된 애플리케이션에서 업데이트를 확인하는 방법을 지정합니다. 자세한 내용은 [방법: ClickOnce 응용 프로그램에 대 한 업데이트 관리](../deployment/how-to-manage-updates-for-a-clickonce-application.md)를 참조 하세요.

### <a name="publish-options-dialog-box"></a>게시 옵션 대화 상자
 게시 옵션 대화 상자에서는 애플리케이션의 배포 옵션을 지정합니다.

|제목|설명|
|-|-|
|[방법: ClickOnce 애플리케이션의 게시 언어 변경](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|지역화된 버전과 일치하도록 언어 및 문화권을 지정하는 방법을 설명합니다.|
|[방법: ClickOnce 애플리케이션의 시작 메뉴 이름 지정](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|ClickOnce 애플리케이션의 표시 이름을 변경하는 방법을 설명합니다.|
|[방법: 기술 지원을 위한 링크 지정](../deployment/how-to-specify-a-link-for-technical-support.md)|사용자가 애플리케이션에 대한 정보를 얻을 수 있는 웹 페이지나 파일 공유를 식별하는 **지원 URL** 속성을 설정하는 방법을 설명합니다.|
|[방법: ClickOnce 배포 시 개별 필수 구성 요소에 대한 지원 URL 지정](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|각 필수 구성 요소에 대한 개별 지원 URL을 포함하도록 애플리케이션 매니페스트를 수동으로 변경하는 방법을 설명합니다.|
|[방법: ClickOnce 애플리케이션의 게시 페이지 지정](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|애플리케이션과 함께 기본 웹 페이지(publish.htm)를 생성 및 게시하는 방법을 설명합니다.|
|[방법: ClickOnce 기본 웹 페이지 사용자 지정](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|자동으로 생성되어 애플리케이션과 함께 게시되는 웹 페이지를 사용자 지정하는 방법을 설명합니다.|
|[방법: CD 설치를 위한 자동 시작 사용](../deployment/how-to-enable-autostart-for-cd-installations.md)|미디어를 삽입할 때 ClickOnce 애플리케이션이 자동으로 시작되도록 자동 시작 기능을 사용하도록 설정하는 방법을 설명합니다.|

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[방법: ClickOnce 애플리케이션에 대한 파일 연결 만들기](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|ClickOnce 애플리케이션에 파일 이름 확장명 지원을 추가하는 방법을 설명합니다.|
|[방법: 온라인 ClickOnce 애플리케이션에서 쿼리 문자열 정보 검색](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|ClickOnce 애플리케이션을 실행하는 데 사용되는 URL에 전달된 매개 변수를 검색하는 방법을 보여 줍니다.|
|[방법: 디자이너를 사용하여 ClickOnce 애플리케이션의 URL 활성화를 사용하지 않도록 설정](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|사용자가 디자이너를 사용하여 **시작** 메뉴에서 애플리케이션을 강제로 시작하도록 하는 방법을 설명합니다.|
|[방법: ClickOnce 애플리케이션의 URL 활성화를 사용하지 않도록 설정](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|사용자가 **시작** 메뉴에서 애플리케이션을 강제로 시작하도록 하는 방법을 설명합니다.|
|[연습: 디자이너를 사용하여 ClickOnce 배포 API에서 요청 시 어셈블리 다운로드](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|애플리케이션 어셈블리를 애플리케이션에서 처음 사용할 때만 디자이너를 사용하여 다운로드하는 방법을 설명합니다.|
|[연습: ClickOnce 배포 API를 사용 하 여 요청 시 어셈블리 다운로드](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|애플리케이션 어셈블리를 애플리케이션에서 처음 사용할 때만 다운로드하는 방법을 설명합니다.|
|[연습: ClickOnce 배포 API를 사용 하 여 요청 시 위성 어셈블리 다운로드](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|위성 어셈블리를 선택적 항목으로 표시하고 클라이언트 컴퓨터의 현재 문화권 설정에 필요한 어셈블리만 다운로드하는 방법을 설명합니다.|
|[연습: 수동으로 ClickOnce 애플리케이션 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|.NET Framework 유틸리티를 사용하여 ClickOnce 애플리케이션을 배포하는 방법을 설명합니다.|
|[연습: 다시 서명할 필요가 없고 브랜딩 정보를 유지 하는 ClickOnce 응용 프로그램을 수동으로 배포](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)|.NET Framework 유틸리티를 사용하여 매니페스트를 다시 서명하지 않고 ClickOnce 애플리케이션을 배포하는 방법을 설명합니다.|
|[방법: 플랫폼을 대상으로 한 프로젝트 구성](../ide/how-to-configure-projects-to-target-platforms.md)|프로젝트에서 **대상 CPU** 또는 **플랫폼 대상** 속성을 변경하여 64비트 프로세서용으로 프로젝트를 게시하는 방법을 설명합니다.|
|[연습: ClickOnce 응용 프로그램을 여러 .NET Framework 버전에서 실행할 수 있도록 설정](https://msdn.microsoft.com/library/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|ClickOnce 애플리케이션을 여러 .NET Framework 버전에 설치하고 실행할 수 있도록 설정하는 방법을 설명합니다.|
|[연습: ClickOnce 응용 프로그램에 대 한 사용자 지정 설치 관리자 만들기](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|ClickOnce 애플리케이션을 설치하는 사용자 지정 설치 관리자를 만드는 방법을 설명합니다.|
|[방법: 시각적 개체 스타일을 사용하여 WPF 애플리케이션 게시](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|비주얼 스타일을 사용하는 WPF 애플리케이션을 게시할 때 발생하는 오류를 해결하기 위한 단계별 지침을 제공합니다.|

## <a name="see-also"></a>추가 정보
- [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce 참조](../deployment/clickonce-reference.md)
