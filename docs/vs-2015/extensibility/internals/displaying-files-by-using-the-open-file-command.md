---
title: 파일 열기 명령을 사용 하 여 파일 표시 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd0018df4efb023357e10ab8050f6cf5e9eba1fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842155"
---
# <a name="displaying-files-by-using-the-open-file-command"></a>파일 열기 명령을 사용하여 파일 표시
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음 단계에서는 IDE에서의 **파일** 메뉴에 있는 **파일 열기** 명령을 처리 하는 방법을 설명 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 또한이 단계에서는 프로젝트가이 명령에서 시작 된 호출에 응답 하는 방법을 설명 합니다.  
  
 사용자가 **파일 메뉴** 에서 **파일 열기** 명령을 클릭 하 고 **파일 열기** 대화 상자에서 파일을 선택 하는 경우 다음 프로세스가 발생 합니다.  
  
1. IDE는 실행 중인 문서 테이블을 사용 하 여 파일이 프로젝트에서 이미 열려 있는지 여부를 확인 합니다.  
  
    - 파일이 열려 있으면 IDE에서 창을 resurfaces 합니다.  
  
    - 파일이 열려 있지 않으면 IDE는를 호출 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 각 프로젝트에 대 한 쿼리를 호출 하 여 파일을 열 수 있는 프로젝트를 확인 합니다.  
  
        > [!NOTE]
        > 의 프로젝트 구현에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 프로젝트가 파일을 여는 수준을 나타내는 우선 순위 값을 제공 합니다. 우선 순위 값은 열거형에 제공 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> .  
  
2. 각 프로젝트는 프로젝트에서 파일을 여는 데 걸리는 중요도를 나타내는 우선 순위 수준으로 응답 합니다.  
  
3. IDE는 다음 기준을 사용 하 여 파일을 열 수 있는 프로젝트를 결정 합니다.  
  
    - 가장 높은 우선 순위 (DP_Intrinsic)로 응답 하는 프로젝트에서 파일을 엽니다. 두 개 이상의 프로젝트가이 우선 순위로 응답 하는 경우 응답 하는 첫 번째 프로젝트에서 파일을 엽니다.  
  
    - 프로젝트가 가장 높은 우선 순위 (DP_Intrinsic)로 응답 하지만 모든 프로젝트가 동일한 우선 순위를 사용 하 여 응답 하는 경우 활성 프로젝트에서 파일을 엽니다. 활성 프로젝트가 없는 경우 응답 하는 첫 번째 프로젝트에서 파일을 엽니다.  
  
    - 프로젝트에서 파일의 소유권을 클레임 하지 않는 경우 (DP_Unsupported) 기타 파일 프로젝트에서 파일을 엽니다.  
  
         기타 파일 프로젝트의 인스턴스를 만드는 경우 프로젝트는 항상 DP_CanAddAsExternal 값으로 응답 합니다. 이 값은 프로젝트에서 파일을 열 수 있음을 나타냅니다. 이 프로젝트는 다른 프로젝트에 없는 열려 있는 파일을 보관 하는 데 사용 됩니다. 이 프로젝트의 항목 목록은 유지 되지 않습니다. 이 프로젝트는 파일을 여는 데 사용 되는 경우에만 **솔루션 탐색기** 표시 됩니다.  
  
         기타 파일 프로젝트에서 파일을 열 수 있는 것으로 표시 되지 않는 경우 프로젝트의 인스턴스가 생성 되지 않은 것입니다. 이 경우 IDE는 기타 파일 프로젝트의 인스턴스를 만들고 프로젝트에 파일을 열도록 지시 합니다.  
  
4. IDE에서 파일을 여는 프로젝트를 확인 하는 즉시 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> 해당 프로젝트에서 메서드를 호출 합니다.  
  
5. 프로젝트에 프로젝트 관련 편집기 또는 표준 편집기를 사용 하 여 파일을 열 수 있는 옵션이 있습니다. 자세한 내용은 [방법: 프로젝트별 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md) 및 [방법: 표준 편집기 각각 열기](../../extensibility/how-to-open-standard-editors.md)를 참조 하세요.  
  
## <a name="see-also"></a>참고 항목  
 [연결 프로그램 명령을 사용 하 여 파일 표시](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)   
 [방법: 프로젝트 관련 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md)   
 [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)
