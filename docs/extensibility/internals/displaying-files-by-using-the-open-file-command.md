---
title: 파일 열기 명령을 사용하여 파일 표시 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc18442c55b6989c4d8668e1425fdd62a2d4b1b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708590"
---
# <a name="display-files-by-using-the-open-file-command"></a>파일 열기 명령을 사용하여 파일 표시
다음 단계에서는 IDE가 의 **파일** 메뉴에서 사용할 수 있는 파일 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **열기** 명령을 처리하는 방법을 설명합니다. 또한 이 명령에서 시작된 호출에 프로젝트가 응답하는 방법에 대해서도 설명합니다.

 사용자가 **파일** 메뉴에서 **파일 열기** 명령을 클릭하고 파일 **열기** 대화 상자에서 파일을 선택하면 다음 프로세스가 수행됩니다.

1. 실행 중인 문서 테이블을 사용하여 IDE는 파일이 프로젝트에서 이미 열려 있는지 여부를 결정합니다.

    - 파일이 열려 있으면 IDE가 창을 다시 서피스를 지정합니다.

    - 파일이 열려 있지 않으면 IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 각 프로젝트를 쿼리하여 파일을 열 수 있는 프로젝트를 결정합니다.

        > [!NOTE]
        > 의 프로젝트 구현에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>프로젝트가 파일을 여는 수준을 나타내는 우선 순위 값을 제공합니다. 우선 순위 값은 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 열거형에 제공됩니다.

2. 각 프로젝트는 파일을 여는 프로젝트에 중점을 두는 중요도를 나타내는 우선 순위 수준으로 응답합니다.

3. IDE는 다음 조건을 사용하여 파일을 여는 프로젝트를 결정합니다.

    - 가장 높은 우선 순위()로`DP_Intrinsic`응답하는 프로젝트가 파일을 엽니다. 두 개 이상의 프로젝트가 이 우선 순위로 응답하는 경우 응답할 첫 번째 프로젝트가 파일을 엽니다.

    - 프로젝트가 가장 높은 우선 순위()로`DP_Intrinsic`응답하지 않지만 모든 프로젝트가 동일한 낮은 우선 순위로 응답하면 활성 프로젝트가 파일을 엽니다. 활성 프로젝트가 없는 경우 응답할 첫 번째 프로젝트가 파일을 엽니다.

    - 프로젝트가 파일()의`DP_Unsupported`소유권을 주장하지 않으면 기타 파일 프로젝트가 파일을 엽니다.

         기타 파일 프로젝트의 인스턴스가 생성되면 프로젝트는 항상 값으로 `DP_CanAddAsExternal`응답합니다. 이 값은 프로젝트가 파일을 열 수 있음을 나타냅니다. 이 프로젝트는 다른 프로젝트에 없는 열린 파일을 보관하는 데 사용됩니다. 이 프로젝트의 항목 목록이 유지되지 않습니다. 이 프로젝트는 파일을 여는 데 사용되는 경우에만 **솔루션 탐색기에서** 볼 수 있습니다.

         기타 파일 프로젝트가 파일을 열 수 있음을 나타내지 않으면 프로젝트의 인스턴스가 만들어지지 않은 것입니다. 이 경우 IDE는 기타 파일 프로젝트의 인스턴스를 만들고 프로젝트에 파일을 열도록 지시합니다.

4. IDE가 파일을 여는 프로젝트를 결정하자마자 해당 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 프로젝트에서 메서드를 호출합니다.

5. 그런 다음 프로젝트에는 프로젝트별 편집기 또는 표준 편집기등을 사용하여 파일을 여는 옵션이 있습니다. 자세한 내용은 [프로젝트별 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md) 및 [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)를 각각 참조하세요.

## <a name="see-also"></a>참조
- [열기 명령을 사용하여 파일 표시](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)
- [방법: 프로젝트별 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md)
- [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)
