---
title: 게시 마법사 (Visual Studio에서 Office 개발)
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5d14abdd9ba6547a3aaf131084168be2e453dd04
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558178"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>게시 마법사 (Visual Studio에서 Office 개발)
  **게시 마법사** 를 사용 하 여 솔루션 파일을 지정 된 위치에 복사 하 고 매니페스트 파일을 만들고 설치 프로그램을 만들 수 있습니다.

 이 마법사에 액세스 하려면 **빌드** 메뉴에서 *SolutionName* **게시** 를 선택 합니다. **솔루션 탐색기**에서 **게시 마법사** 에 액세스할 수도 있습니다. 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **게시**를 선택 합니다.

 아래 각 섹션에서는 마법사의 페이지에 대해 설명 합니다.

## <a name="where-do-you-want-to-publish-the-application"></a>응용 프로그램을 게시할 위치를 선택 하십시오.
 **이 응용 프로그램을 게시할 위치를 지정 하십시오** . 필수. 게시 위치는 **게시 마법사** 가 매니페스트, 어셈블리, 임시 인증서 및 기타 파일 등의 솔루션 파일을 빌드에서 복사 하는 디렉터리입니다. 이 디렉터리에 쓰기 권한이 있어야 합니다.

 위치를 디스크 경로, 파일 공유, FTP 사이트 또는 웹 사이트 URL로 입력 하거나 **찾아보기** 단추를 클릭 하 여 위치를 찾습니다. 경로는 다음 형식으로 지정할 수 있습니다.

- 표준 Windows 형식의 상대 또는 절대 경로 (예: *C:\deploy\myapplication* 또는 *\myapplication*)

- *\\\ServerName\MyApplication\\* 와 같은 UNC (범용 명명 규칙) 경로입니다.

- `http://www.contoso.com/MyApplication`와 같은 웹 사이트의 URL입니다.

  Iis가 설치 되어 있는 경우 기본적으로 게시 위치는 *http://localhost/projectname/* 이 고, iis를 설치 하지 않은 경우에는 publish \ 디렉터리입니다.

> [!NOTE]
> 대상 컴퓨터에서 Windows Vista를 실행 하는 경우에는 더 많은 고려 사항이 있습니다. 로컬 게시 옵션을 사용 하려면 Windows Vista 컴퓨터의 관리자 여야 합니다. 또한 IIS의 설치 여부에 관계 없이 기본 위치는 항상 *게시\\* 디렉터리입니다.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>최종 사용자 컴퓨터의 기본 설치 경로는 무엇입니까?
 설치 경로는 선택 사항입니다. 원할 경우 나중에 설치 경로를 설정할 수 있습니다. 자세한 내용은 [방법: Office 솔루션의 설치 경로 변경](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)을 참조 하십시오.

 설치 경로는 최종 사용자가 사용자 지정을 설치 하는 디렉터리입니다. 또한 솔루션에서 업데이트를 확인하는 데 사용하는 경로이기도 합니다. 이전 페이지에서 **이 응용 프로그램을 게시할 위치 지정** 상자에 입력 한 경로와 경로가 동일 하지 않으면 **게시 마법사** 는이 위치에 솔루션을 배포 하지 않습니다.

 **웹 사이트에서** 솔루션을 설치 하기 위해 최종 사용자가 따라야 하는 URL을 지정 합니다.

 **UNC 경로 또는 파일 공유에서** 최종 사용자가 솔루션을 설치 하기 위해 수행할 UNC 경로를 지정 합니다.

 Cd-rom **또는 Dvd-rom에서** 이 옵션에는 설치 경로가 필요 하지 않습니다.

 Visual Studio는 CD 또는 DVD를 굽지 않습니다. 출력을 CD 또는 DVD에 수동으로 복사 해야 합니다.

## <a name="see-also"></a>참고 항목
- [ClickOnce를 사용 하 여 Office 솔루션 배포](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Visual Studio에서 프로젝트 디자이너 &#40;, 게시 페이지&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
