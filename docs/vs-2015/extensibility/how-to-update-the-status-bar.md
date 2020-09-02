---
title: '방법: 상태 표시줄 업데이트 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d48b07dd5e4fc1fe745e3669041884c1b8eacd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703140"
---
# <a name="how-to-update-the-status-bar"></a>방법: 상태 표시줄 업데이트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**상태 표시줄** 은 하나 이상의 상태 텍스트 선이나 표시기를 포함 하는 여러 응용 프로그램 창의 아래쪽에 있는 컨트롤 막대입니다.  
  
### <a name="to-update-the-status-bar"></a>상태 표시줄을 업데이트 하려면  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>폼 보기 및 코드 뷰와 같이 편집기에서 제공 하는 각 개별 뷰 개체 (DocView)에 대해을 구현 합니다.  
  
2. IDE가를 호출 하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 의 메서드를 호출 하 여 **상태 표시줄** 의 정보를 업데이트 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> .  
  
    > [!NOTE]
    > IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> 문서 창이 처음 활성화 된 경우에만를 호출 합니다. 문서 창이 활성 상태인 나머지 시간 동안 편집기의 상태가 변경 됨에 따라 **상태 표시줄** 정보를 업데이트 해야 합니다.  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 **상태 표시줄** 에는 다음 4 개의 개별 필드가 포함 됩니다.  
  
- 상태 텍스트  
  
- 진행률 표시줄  
  
- 애니메이션 아이콘  
  
- 편집기 정보  
  
  자세한 내용은 [상태 표시줄](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)을 참조 하세요.  
  
  IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 문서 창이 활성화 될 때 구현 메서드를 자동으로 호출 합니다.  
  
  VSPackage 구현자는 상태 표시줄의 상태 텍스트를 업데이트 해야 합니다. 상태 텍스트 필드가 유휴 시간에 빈 텍스트 ("")로 설정 된 경우 IDE는이 문자열을 "READY"로 다시 설정 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [상태 표시줄](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)
