---
title: 참조 페이지, 프로젝트 디자이너(Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
- Unused References dialog box
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8bb18ec8dd12431d650d844e3698c1986c8d8bd8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665636"
---
# <a name="references-page-project-designer-visual-basic"></a>참조 페이지, 프로젝트 디자이너(Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**프로젝트 디자이너**의 **참조** 페이지를 사용하여 프로젝트에서 참조, 웹 참조 및 가져온 네임스페이스를 관리합니다. 프로젝트에는 COM 구성 요소, XML 웹 서비스, .NET Framework 클래스 라이브러리나 어셈블리 또는 기타 클래스 라이브러리에 대한 참조가 포함될 수 있습니다. 참조 사용에 대한 자세한 내용은 [프로젝트의 참조 관리](../../ide/managing-references-in-a-project.md)를 참조하세요.

 **참조** 페이지에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드(**솔루션** 노드 아님)를 선택합니다. 그런 다음 메뉴 모음에서 **프로젝트**, **속성**을 선택합니다. 프로젝트 디자이너가 나타나면 **참조** 탭을 클릭합니다.

## <a name="uielement-list"></a>UIElement 목록
 다음 옵션을 사용하여 프로젝트에서 참조 및 가져온 네임스페이스를 선택하거나 제거할 수 있습니다.

 **사용 하지 않는 참조** **사용 하지 않는 참조** 대화 상자에 액세스 하려면이 단추를 클릭 합니다.

 **사용하지 않는 참조** 대화 상자에서는 프로젝트에 포함된 참조를 제거할 수 있지만 실제로 코드에 사용되는 참조는 제거할 수 없습니다. 이 대화 상자에는 **참조 이름**, **경로** 및 프로젝트에서 사용하지 않는 네임스페이스 참조에 대한 기타 정보를 나열하는 표가 있습니다. 프로젝트에서 제거할 네임스페이스를 표에서 선택하고 **제거**를 클릭합니다.

 **참조 경로** **참조 경로** 대화 상자에 액세스 하려면이 단추를 클릭 합니다.

> [!NOTE]
> 프로젝트 시스템이 어셈블리 참조를 찾으면 시스템에서는 다음 순서로 다음 위치를 확인하여 참조를 확인합니다.
>
> 1. 프로젝트 폴더. 프로젝트 폴더 파일은 **모든 파일 표시**가 적용되지 않을 경우 **솔루션 탐색기**에 표시됩니다.
>    2. **참조 경로** 대화 상자에 지정된 폴더.
>    3. **참조 추가** 대화 상자에 파일을 표시하는 폴더.
>    4. 프로젝트의 obj 폴더. COM 참조를 프로젝트에 추가하면 하나 이상의 어셈블리가 프로젝트의 obj 폴더에 추가될 수 있습니다.

 **참조** 이 목록에는 사용 되거나 사용 되지 않는 프로젝트의 모든 참조가 표시 됩니다.

 **추가** 참조 또는 웹 참조를 **참조 목록에** 추가 하려면이 단추를 클릭 합니다.

 [참조 추가] 대화 상자를 사용하여 참조를 프로젝트에 추가하려면 **참조**를 선택합니다.

 [웹 참조 추가] 대화 상자를 사용하여 웹 참조를 프로젝트에 추가하려면 **웹 참조**를 선택합니다.

 **제거** **참조** 목록에서 하나 이상의 참조를 선택 하 고이 단추를 클릭 하 여 삭제 합니다.

 **웹 참조 업데이트** **참조** 목록에서 웹 참조를 선택 하 고이 단추를 클릭 하 여 업데이트 합니다.

 **가져온 네임 스페이스** 이 상자에 사용자 고유의 네임 스페이스를 입력 하 고 **사용자 가져오기 추가** 를 클릭 하 여 네임 스페이스 목록에 추가할 수 있습니다.

 사용자가 가져온 네임스페이스의 별칭을 만들 수 있습니다. 이렇게 하려면 별칭 및 형식 *별칭* = *네임 스페이스*에 네임 스페이스를 입력 합니다. 긴 네임스페이스를 사용할 경우 이 방법이 유용합니다(예: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`).

 **사용자 가져오기 추가** **가져온 네임 스페이스 상자에** 지정 된 네임 스페이스를 가져온 네임 스페이스 목록에 추가 하려면이 단추를 클릭 합니다. 이 단추는 지정된 네임스페이스가 목록에 없는 경우에만 활성화됩니다.

 **네임 스페이스 목록** 이 목록에는 사용 가능한 모든 네임 스페이스가 표시 됩니다. 프로젝트에 포함된 네임스페이스의 확인란이 선택됩니다.

 **사용자 가져오기 업데이트** 네임 스페이스 목록에서 사용자 지정 네임 스페이스를 선택 하 고 **가져온** 네임 스페이스 상자에서 바꾸려는 이름을 입력 한 다음이 단추를 클릭 하 여 새 네임 스페이스를 변경 합니다. 이 단추는 선택된 네임스페이스가 **사용자 가져오기 추가** 단추를 사용하여 목록에 추가한 네임스페이스인 경우에만 활성화됩니다. 다음을 추가할 수 있습니다.

- 클래스 또는 네임스페이스(예: <xref:System.Math?displayProperty=fullName>).

- 별칭이 지정된 가져오기(예: `VB=Microsoft.VisualBasic`).

- XML 네임스페이스(예: `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`).

## <a name="see-also"></a>관련 항목
 [NIB 방법: 참조 추가 대화 상자를 사용 하 여 참조 추가 또는 제거](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) [방법: 가져온 네임 스페이스 추가 또는 제거 (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md) [NIB: 웹 참조 추가 대화 상자](https://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5) [Imports 문 (XML 네임 스페이스)](https://msdn.microsoft.com/library/1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4)
