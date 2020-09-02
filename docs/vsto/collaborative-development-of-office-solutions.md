---
title: Office 솔루션 공동 개발
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 76c26a110d88d3dee8bf7540647ea0bfde4e7c4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62949489"
---
# <a name="collaborative-development-of-office-solutions"></a>Office 솔루션 공동 개발
  여러 개발자가 다른 Visual Studio 프로젝트에서 공동 작업 하는 것과 동일한 방식으로 Office 프로젝트에서 작업할 수 있습니다. Office가 서로 다른 위치에 설치 된 경우에도 Visual Studio에서는 각 컴퓨터에서 Microsoft Office 설치를 올바르게 찾습니다. 그러나 알아야 할 몇 가지 중요 한 고려 사항이 있습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="debug-properties-are-not-shared"></a>디버그 속성이 공유 되지 않습니다.
 디버그 속성은 소스 제어에서 여러 사용자 간에 공유되지 않습니다. Visual Basic 및 Visual c # 프로젝트는 디버깅 속성을 사용자별 파일 (*projectname*. 사용자 또는 *projectname*. 사용자)에 저장 하며,이 파일은 소스 제어에서 사용 되지 않습니다. 둘 이상의 사용자를 디버깅하는 경우 각 사용자가 디버그 속성을 수동으로 입력해야 합니다.

 프로젝트가 원본 제어 대신 네트워크 공유에 있는 경우 공동 개발자가 솔루션을 열고 어셈블리를 테스트할 수 있도록 몇 가지 추가 단계를 수행 해야 합니다.

## <a name="source-control-requires-checking-out-all-files"></a>소스 제어에서 모든 파일을 체크 아웃 해야 합니다.
 프로젝트에 소스 제어를 사용 하는 경우 기본적으로 숨겨진 파일을 비롯 하 여 코드 파일을 변경할 때마다 **솔루션 탐색기** 의 코드 파일 ( *ThisDocument*, *ThisWorkbook*또는 *ThisAddIn* 코드 파일) 아래의 모든 파일을 체크 아웃 해야 합니다. 최상위 코드 파일만 체크 아웃 하면 변경 내용이 손실 될 수 있습니다.

 변경을 수행한 후에는 모든 파일을 다시 확인 합니다. 프로젝트의 숨겨진 코드 파일에 대 한 자세한 내용은 [Visual Studio 환경의 Office 프로젝트](../vsto/office-projects-in-the-visual-studio-environment.md)를 참조 하세요.

## <a name="security-for-informal-collaboration-on-a-network"></a>네트워크에서 비공식적 공동 작업을 위한 보안
 네트워크 위치 (예: Servername Sharename)에 있는 모든 문서 수준 솔루션에 대해 \\ \\ *Servername* \\ *Sharename*작업 중인 Microsoft Office 응용 프로그램의 신뢰할 수 있는 폴더 목록에 정규화 된 위치를 추가 해야 합니다. 주 폴더 아래에 하위 디렉터리를 포함 하는 옵션을 선택 하거나, 명시적으로 디버그 및 빌드 폴더를 신뢰할 수 있는 폴더 목록에 추가 합니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 [문서에 신뢰 부여](../vsto/granting-trust-to-documents.md)를 참조 하세요.

 빌드 시 자동으로 생성 되는 임시 인증서는 암호로 보호 되지 않습니다. 인증서에는 개발자의 로그인 이름 및 기타 개인 정보가 포함 되어 있습니다. 임시 인증서로 서명 된 사용자 지정 항목을 배포 하는 경우 다른 사용자가이 정보에 액세스할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
- [Office 솔루션 빌드](../vsto/building-office-solutions.md)
