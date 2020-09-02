---
title: 옵션 대화 상자, 환경, 문서 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
- VS.ToolsOptionsPag.Environment.Documents
helpviewer_keywords:
- Documents Environment Options dialog box
- defaults, directories
- error messages, customizing
- files [Visual Studio], default options
- files [Visual Basic], auto-loading modified
- windows, customizing environment
- in-memory editing
- folders [Visual Studio], specifying where Open File goes
- Open File dialog box
- windows, enabling re-use of current
- notifications, files changed
- files [Visual Studio], displaying in Solution Explorer
- default directories
- read-only files, editing
- Options dialog box, showing Miscellaneous Files
- directories [Visual Studio], IDE environment options
- Options dialog box, Documents page
- warnings, files changed
- Solution Explorer, displaying files in
ms.assetid: 4e3ccf1b-cd68-4db6-9470-710c911b47fc
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 705b1a5992d1a3e7931c316c713d46e7e8c7f72e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657776"
---
# <a name="documents-environment-options-dialog-box"></a>옵션 대화 상자, 환경, 문서
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**옵션** 대화 상자의 이 페이지를 사용하여 IDE(통합 개발 환경)에서 문서 표시를 제어하고 문서 및 파일에 대한 외부 변경 내용을 관리합니다. 이 대화 상자에 액세스하려면 **도구** 메뉴에서 **옵션**을 클릭하고 **환경** 노드에서 **문서**를 선택합니다. **문서**가 목록에 나타나지 않으면 **옵션** 대화 상자에서 **모든 설정 표시**를 선택합니다.

> [!NOTE]
> 대화 상자에서 사용할 수 있는 옵션과 메뉴 명령의 이름 및 위치는 실제 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.

 **저장되면 현재 문서 창 다시 사용** 이 옵션을 선택하면 저장된 현재 문서가 닫히고 새 문서가 같은 창에서 열립니다. 현재 문서가 저장되지 않은 경우에는 문서가 열려 있고 새 문서가 별도의 창에서 열립니다. 이 옵션을 선택 취소하면 새 문서가 항상 별도의 창에서 열립니다.

 다중 문서 잘라내기 및 붙여넣기 작업을 자주 수행하지 않는 경우 작업 공간에서 열린 문서 및 창 수를 최소화하려면 이 옵션을 시도하세요.

 **파일이 환경 외부에서 변경되면 검색** 이 옵션을 선택하면 IDE 외부에서 편집기를 통해 적용된 열린 파일의 변경 내용에 대한 메시지가 제공됩니다. 메시지를 통해 스토리지에서 파일을 다시 로드할 수 있습니다.

 **저장되면 변경 내용 자동 로드****파일이 환경 외부에서 변경되면 검색**을 선택하고 IDE의 열린 파일을 IDE 외부에서 변경하는 경우 기본적으로 경고 메시지가 생성됩니다. 이 옵션을 사용하도록 설정하면 경고가 나타나지 않고 외부 변경 내용을 선택하도록 문서가 IDE에 다시 로드됩니다.

 **읽기 전용 파일 편집 허용(저장할 때 경고 표시)** 이 옵션을 사용하면 읽기 전용 파일을 열고 편집할 수 있습니다. 작업을 완료하고 변경 내용 레코드를 저장할 때 새 이름으로 파일을 저장하려면 **다른 이름으로 저장** 명령을 사용해야 합니다.

 **현재 활성 문서의 디렉터리를 사용하여 파일 열기** 이 옵션을 선택하면 **파일 열기** 대화 상자에 활성 문서의 디렉터리가 표시되도록 지정합니다. 이 옵션을 선택 취소하면 **파일 열기** 대화 상자에 파일을 여는 데 마지막으로 사용되는 디렉터리가 표시됩니다.

 **로드할 때 줄 끝 일관성 검사** 편집기에서 파일의 줄 끝을 검색하고 줄 끝 형식 지정 방법이 일치하지 않는 것을 발견할 경우 메시지 상자를 표시하게 하려면 이 옵션을 선택합니다.

 **전체 실행 취소로 인해 편집된 파일이 수정될 때 경고 표시****전체 실행 취소** 명령이 리팩터링 작업 후에 변경된 파일에 적용된 리팩터링 변경 내용을 롤백할 경우 메시지를 표시하려면 이 옵션을 선택합니다. 파일을 리팩터링 전 상태로 되돌리려면 파일에 적용된 후속 변경 내용이 취소될 수 있습니다.

 **솔루션 탐색기에 기타 파일 표시****솔루션 탐색기**에서 **기타 파일** 노드를 표시하려면 이 옵션을 선택합니다. 기타 파일은 프로젝트나 솔루션과 연결되지 않은 파일이지만, 편의를 위해 **솔루션 탐색기**에 표시될 수 있습니다.

> [!NOTE]
> 활성 웹 응용 프로그램에 포함 되지 않은 웹 문서에 대 한 **파일** 메뉴에서 **브라우저에서 보기** 명령을 사용 하려면이 옵션을 선택 합니다.

 ** \<** *n* **> 기타 파일 프로젝트에 저장 된 항목** 은 **솔루션 탐색기**의 **MiscellaneousFiles** 폴더에 유지할 파일 수를 지정 합니다. 이러한 파일은 편집기에서 더 이상 열려 있지 않은 경우에도 나열됩니다. 0~256의 정수를 지정할 수 있습니다. 기본 개수는 0개입니다.

 예를 들어 이 옵션을 5로 설정하고 10개의 기타 파일이 열려 있으면 10개 파일을 모두 닫을 때 처음 5개가 **기타 파일** 폴더에 계속 표시됩니다.

 **데이터를 코드 페이지에 저장할 수 없을 때 문서를 유니코드로 저장** 선택한 코드 페이지와 호환되지 않는 정보가 포함된 파일이 기본적으로 유니코드로 저장되도록 하려면 이 옵션을 선택합니다.

## <a name="see-also"></a>관련 항목
 [환경 옵션 대화 상자](../../ide/reference/environment-options-dialog-box.md) [기타 파일](../../ide/reference/miscellaneous-files.md) [텍스트 찾기 및 바꾸기](../../ide/finding-and-replacing-text.md)
