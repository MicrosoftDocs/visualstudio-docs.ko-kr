---
title: 프로젝트 디자이너, 게시 페이지 (Office 개발)
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 86d575b254209b547504ea6d746d03853990bfb4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328994"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>게시 페이지, 프로젝트 디자이너 (Visual Studio에서 Office 개발)
  **프로젝트 디자이너** 의 **게시** 페이지를 통해 배포를 위한 속성을 구성합니다.

 이 페이지에 액세스하려면 **솔루션 탐색기**에서 프로젝트를 선택한 다음 **프로젝트** 메뉴에서 *Projectname* **속성**을 선택합니다. **게시** 페이지가 표시되지 않으면 **게시** 탭을 선택합니다.

> [!NOTE]
> 게시 위치를 **게시 마법사**에서 설정할 수도 있습니다. 자세한 내용은 [방법: ClickOnce를 사용 하 여 Office 솔루션 게시](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)를 참조 하세요.

## <a name="uielement-list"></a>UI 요소 목록
 **폴더 위치 게시 (웹 사이트, ftp 서버 또는 파일 경로)** 필수.

 게시 폴더 위치는 Visual Studio가 빌드에서 매니페스트, 어셈블리 및 기타 파일과 같은 솔루션 파일을 복사하는 디렉터리입니다. 이 디렉터리에 쓰기 권한이 있어야 합니다.

 옵션에는 로컬 컴퓨터, UNC 파일 공유 또는 HTTP/HTTPS 웹 사이트가 포함됩니다. 경로는 local (*c:\foldername\publishfolder*), 상대 (*게시 \\ *) 또는 정규화 된 위치 (* \\ \servername\foldername* 또는 http://<em>servername/foldername</em>)가 될 수 있습니다.

 기본적으로 게시 위치는 IIS를 *http://localhost/projectname/* 설치한 경우이 고, iis를 설치 하지 않은 경우에는 *publish \\ * 디렉터리입니다.

 **설치 폴더 URL** 필드.

 설치 폴더 URL은 최종 사용자가 사용자 지정을 설치하는 디렉터리입니다. 또한 솔루션에서 업데이트를 확인하는 데 사용하는 경로이기도 합니다. 경로는 게시 폴더 위치와 동일할 수 있지만 이것이 요구 사항은 아닙니다.

 옵션에는 로컬 컴퓨터, UNC 파일 공유 또는 HTTP/HTTPS 웹 사이트가 포함됩니다. 경로는 local (*c:\foldername\publishfolder*), 상대 (*게시 \\ *) 또는 정규화 된 위치 (* \\ \servername\foldername* 또는 http://<em>servername/foldername</em>)가 될 수 있습니다. 모든 HTTP/HTTPS 위치는 US ASCII 문자로 만들어야 합니다. 유니코드 문자는 지원되지 않습니다.

 설치 경로가 설정된 경우 사용자가 사용자 지정을 설치하려면 해당 위치에 사용자 지정 파일이 있어야 합니다. 최종 배포 위치를 알고 있는 경우에만 위치를 설정해야 합니다.

 설치 파일이 CD 옵션 사용과 같이 문서 또는 설치 프로그램의 상대적인 위치에 있는 경우 이 상자를 비워 둡니다.

 이 값은 관리자가 나중에 할당할 수 있습니다. 자세한 내용은 [방법: Office 솔루션의 설치 경로 변경](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)을 참조 하세요.

 **필수 조건** 필수 구성 요소는 설치 프로그램에 포함 되거나 설치 중에 필요할 때 다운로드할 수 있습니다.

- **구성 요소 공급업체의 웹 사이트에서 필수 조건 다운로드**: 이 옵션을 사용하여 Microsoft에서 이러한 필수 조건을 다운로드합니다.

- **내 애플리케이션과 동일한 위치에서 필수 조건 다운로드**: 이 옵션을 사용하여 설치 관리자에서 필수 조건을 패키지에 포함시킵니다. 설치 프로그램에 필수 조건 파일을 포함하면 솔루션 크기가 늘어납니다.

- **다음 위치에서 필수 조건 다운로드**: 이 옵션을 사용하여 웹 페이지 또는 네트워크 공유의 다른 설치 프로그램처럼 필수 조건을 최종 사용자가 개별적으로 사용할 수 있게 합니다.

  **업데이트** 업데이트 간격은 솔루션이 업데이트를 확인 하는 빈도를 결정 합니다. 기본값은 7일마다 확인하는 것입니다.

  문서 수준 사용자 지정 또는 VSTO 추가 기능이 로드될 때마다 업데이트를 확인하면 지속적으로 업데이트는 되지만 시작 성능에 영향을 줍니다.

  CD 또는 이동식 드라이브를 사용하여 배포하는 경우 이 옵션을 **업데이트 확인 안 함**으로 설정합니다.

  **옵션 (설명)** 다음 속성에 대 한 게시 옵션을 설정할 수 있습니다.

- 게시 언어: Office 솔루션의 로캘

- 게시자 이름: **프로그램 추가/제거** 또는 **프로그램 및 기능**에 표시되는 회사 또는 개발자 이름

- 제품 이름: **프로그램 추가/제거** 또는 **프로그램 및 기능**에 표시되는 Office 솔루션의 이름

- 지원 URL: 최종 사용자가 Office 솔루션에 대한 기술 지원에 문의하는 위치

  **옵션 (Office 설정)** 다음 속성에 대 한 게시 옵션을 설정할 수 있습니다.

- 솔루션 이름: Office 애플리케이션에 표시되는 Office 솔루션의 이름

- 설명: Office 애플리케이션에 표시되는 Office 솔루션에 대한 설명

- VSTO 추가 기능 로드 동작

  - 시작 시 로드: Office 애플리케이션이 시작될 때 VSTO 추가 기능이 로드되도록 지정합니다.

  - 요청 시 로드: 사용자가 VSTO 추가 기능의 기능을 사용하는 UI 요소를 클릭할 때처럼 VSTO 추가 기능이 애플리케이션에서 필요로 할 때 로드되도록 지정합니다.

  **게시 언어** 이 옵션은 Microsoft 소프트웨어 사용 조건의 언어를 설정 하 고 필수 조건 목록에 언어 팩을 포함 합니다. 사용자 지정의 언어에는 영향을 주지 않습니다. 설치 프로그램의 언어는 Visual Studio의 설치된 언어에 의해 결정됩니다.

  **게시 언어**를 변경 하는 방법에 대 한 자세한 내용은 [방법: ClickOnce 응용 프로그램의 게시 언어 변경](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)을 참조 하세요.

  **게시 버전** 사용자 지정의 버전 번호를 설정 합니다. 버전 번호가 변경되면 애플리케이션이 업데이트로 게시됩니다. 이전에 게시된 버전을 덮어쓰지 않도록 빌드 프로세스 동안 각 버전에 대해 새 폴더가 만들어집니다. 게시 버전의 각 부분(**주**, **부**, **빌드**, **수정**)에는 최대 5개의 숫자가 포함될 수 있습니다.

  **릴리스할 때마다 자동으로 수정 번호 증가** 필드. 선택된 경우(기본값), 버전 번호의 **수정** 부분이 사용자 지정을 게시할 때마다 1씩 증가합니다. 그러면 사용자 지정이 업데이트로 게시됩니다.

  **지금 게시** 현재 설정을 사용 하 여 응용 프로그램을 게시 합니다. **게시 마법사** 의 **마침**단추와 동일합니다.

## <a name="see-also"></a>추가 정보

- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
- [ClickOnce를 사용 하 여 Office 솔루션 배포](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [배포를 위한 Office 솔루션 필수 조건](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e)
