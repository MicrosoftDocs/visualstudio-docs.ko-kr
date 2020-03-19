---
title: 참조 페이지, 프로젝트 디자이너(Visual Basic)
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b80427999ad841c493e61cd704b64435f81c3914
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565606"
---
# <a name="references-page-project-designer-visual-basic"></a>참조 페이지, 프로젝트 디자이너(Visual Basic)

**프로젝트 디자이너**의 **참조** 페이지를 사용하여 프로젝트에서 참조, 웹 참조 및 가져온 네임스페이스를 관리합니다. 프로젝트에는 COM 구성 요소, XML 웹 서비스, .NET 라이브러리나 어셈블리 또는 기타 클래스 라이브러리에 대한 참조가 포함될 수 있습니다. 참조 사용에 대한 자세한 내용은 [프로젝트의 참조 관리](../../ide/managing-references-in-a-project.md)를 참조하세요.

**참조** 페이지에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드(**솔루션** 노드 아님)를 선택합니다. 그런 다음 메뉴 모음에서 **프로젝트**, **속성**을 선택합니다. 프로젝트 디자이너가 나타나면 **참조** 탭을 클릭합니다.

## <a name="uielement-list"></a>UIElement 목록

다음 옵션을 사용하여 프로젝트에서 참조 및 가져온 네임스페이스를 선택하거나 제거할 수 있습니다.

**참조 경로**

**참조 경로** 대화 상자에 액세스하려면 이 단추를 클릭합니다.

> [!NOTE]
> 프로젝트 시스템이 어셈블리 참조를 찾으면 시스템에서는 다음 순서로 다음 위치를 확인하여 참조를 확인합니다.
>
> 1. 프로젝트 폴더. 프로젝트 폴더 파일은 **모든 파일 표시**가 적용되지 않을 경우 **솔루션 탐색기**에 표시됩니다.
> 2. **참조 경로** 대화 상자에 지정된 폴더.
> 3. **참조 추가** 대화 상자에 파일을 표시하는 폴더.
> 4. 프로젝트의 obj 폴더. COM 참조를 프로젝트에 추가하면 하나 이상의 어셈블리가 프로젝트의 obj 폴더에 추가될 수 있습니다.

 **참조**

이 목록에는 프로젝트에 있는 사용되거나 사용되지 않은 모든 참조가 표시됩니다.

 **추가**

참조 또는 웹 참조를 **참조** 목록에 추가하려면 이 단추를 클릭합니다.

[참조 추가] 대화 상자를 사용하여 참조를 프로젝트에 추가하려면 **참조**를 선택합니다.

**웹 참조 추가** 대화 상자를 사용하여 웹 참조를 프로젝트에 추가하려면 **웹 참조**를 선택합니다.

 **제거**

**참조** 목록에서 하나 이상의 참조를 선택하고 나서 이 단추를 클릭하여 참조를 삭제합니다.

 **웹 참조 업데이트**

**참조** 목록에서 웹 참조를 선택하고 이 단추를 클릭하여 웹 참조를 업데이트합니다.

 **가져온 네임스페이스**

이 상자에서 고유한 네임스페이스를 입력하고 **사용자 가져오기 추가**를 클릭하여 네임스페이스 목록에 네임스페이스를 추가합니다.

사용자가 가져온 네임스페이스의 별칭을 만들 수 있습니다. 이 작업을 하려면 *별칭*=*네임스페이스* 형식으로 별칭 및 네임스페이스를 입력합니다. 긴 네임스페이스를 사용할 경우 이 방법이 유용합니다(예: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`).

 **사용자 가져오기 추가**

**가져온 네임스페이스** 상자에 지정된 네임스페이스를 가져온 네임스페이스 목록에 추가하려면 이 단추를 클릭합니다. 이 단추는 지정된 네임스페이스가 목록에 없는 경우에만 활성화됩니다.

 **네임스페이스 목록**

이 목록에는 모든 사용 가능한 네임스페이스가 표시됩니다. 프로젝트에 포함된 네임스페이스의 확인란이 선택됩니다.

 **사용자 가져오기 업데이트**

네임스페이스 목록에서 사용자가 지정한 네임스페이스를 선택하고, **가져온 네임스페이스** 상자에서 해당 네임스페이스를 대체할 이름을 입력하고 나서, 이 단추를 클릭하여 새 네임스페이스로 변경합니다. 이 단추는 선택된 네임스페이스가 **사용자 가져오기 추가** 단추를 사용하여 목록에 추가한 네임스페이스인 경우에만 활성화됩니다. 다음을 추가할 수 있습니다.

- 클래스 또는 네임스페이스(예: <xref:System.Math?displayProperty=fullName>).

- 별칭이 지정된 가져오기(예: `VB=Microsoft.VisualBasic`).

- XML 네임스페이스(예: `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`).

## <a name="see-also"></a>참고 항목

- [프로젝트의 참조 관리](../../ide/managing-references-in-a-project.md)
- [방법: 가져온 네임스페이스 추가 또는 제거(Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)
- [Imports 문(XML 네임스페이스)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)
