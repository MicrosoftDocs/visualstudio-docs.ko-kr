---
title: 옵션 대화 상자, 환경, 문서
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.Environment.Documents
- VS.ToolsOptionsPages.Environment.Documents
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7813a2e7686bef5a146e7472bce7f2c24baf9cd2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570065"
---
# <a name="options-dialog-box-environment--documents"></a>옵션 대화 상자: 환경 \> 문서

**옵션** 대화 상자의 이 페이지를 사용하여 IDE(통합 개발 환경)에서 문서 표시를 제어하고 문서 및 파일에 대한 외부 변경 내용을 관리합니다. 이 대화 상자에 액세스하려면 **도구** 메뉴에서 **옵션**을 클릭하고 **환경** > **문서**를 선택합니다.

**파일이 환경 외부에서 변경되면 검색**

이 옵션을 선택하면 IDE 외부에서 편집기를 통해 적용된 열린 파일의 변경 내용에 대한 메시지가 제공됩니다. 메시지를 통해 스토리지에서 파일을 다시 로드할 수 있습니다.

**저장하지 않은 변경 내용이 없으면 수정된 파일을 다시 로드**

**파일이 환경 외부에서 변경되면 검색**이 선택되고 IDE의 열린 파일이 IDE 외부에서 변경된 경우 기본적으로 경고 메시지가 생성됩니다. 이 옵션을 사용하도록 설정하면 경고가 나타나지 않고 외부 변경 내용을 선택하도록 문서가 IDE에 다시 로드됩니다.

**읽기 전용 파일 편집 허용(저장할 때 경고 표시)**

이 옵션을 사용하도록 설정하면 읽기 전용 파일을 열고 편집할 수 있습니다. 작업이 완료된 후 변경 내용 레코드를 저장하려면 **다른 이름으로 저장** 명령을 사용하여 파일을 새 이름으로 저장해야 합니다.

**현재 활성 문서의 디렉터리를 사용하여 파일 열기**

이 옵션을 선택하면 이 옵션은 **파일 열기** 대화 상자에 활성 문서의 디렉터리가 표시되도록 지정합니다. 이 옵션을 선택 취소하면 **파일 열기** 대화 상자에 파일을 여는 데 마지막으로 사용되는 디렉터리가 표시됩니다.

**로드할 때 줄 끝 일관성 검사**

편집기에서 파일의 줄 끝을 검색하고 줄 끝 형식 지정 방법이 일치하지 않는 것을 발견할 경우 메시지 상자를 표시하게 하려면 이 옵션을 선택합니다.

**전체 실행 취소로 인해 편집된 파일이 수정될 때 경고 표시**

**전체 실행 취소** 명령이 리팩터링 작업 후에 변경된 파일에 적용된 리팩터링 변경 내용을 롤백할 경우 메시지를 표시하려면 이 옵션을 선택합니다. 파일을 리팩터링 전 상태로 되돌리려면 파일에 적용된 후속 변경 내용이 취소될 수 있습니다.

**솔루션 탐색기에 기타 파일 표시**

**솔루션 탐색기**에서 **기타 파일** 노드를 표시하려면 이 옵션을 선택합니다. 기타 파일은 프로젝트나 솔루션과 연결되지 않은 파일이지만, 편의를 위해 **솔루션 탐색기**에 표시될 수 있습니다.

> [!NOTE]
> 활성 웹 애플리케이션에 포함되지 않은 웹 문서의 경우 **파일** 메뉴에서 **브라우저에서 보기** 명령을 사용하도록 설정하려면 이 옵션을 선택합니다.

**기타 파일 프로젝트에 저장된 항목**

**솔루션 탐색기**의 **기타 파일** 폴더에서 유지할 파일 수를 지정합니다. 이러한 파일은 편집기에서 더 이상 열려 있지 않은 경우에도 나열됩니다. 0~256의 정수를 지정할 수 있습니다. 기본 개수는 0개입니다.

예를 들어 이 옵션을 5로 설정하고 10개의 기타 파일이 열려 있으면 10개 파일을 모두 닫을 때 처음 5개가 **기타 파일** 폴더에 계속 표시됩니다.

**데이터를 코드 페이지에 저장할 수 없을 때 문서를 유니코드로 저장**

선택된 코드 페이지와 호환되지 않는 정보가 포함된 파일이 기본적으로 유니코드로 저장되도록 하려면 이 옵션을 선택합니다.

## <a name="see-also"></a>참조

- [기타 파일](../../ide/reference/miscellaneous-files.md)
- [텍스트 찾기 및 바꾸기](../../ide/finding-and-replacing-text.md)
