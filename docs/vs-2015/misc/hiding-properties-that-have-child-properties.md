---
title: 자식 속성을 가진 속성 숨기기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d20b865c6f07d76320a7df8402810c82869ddfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822388"
---
# <a name="hiding-properties-that-have-child-properties"></a>자식 속성을 가진 속성 숨기기
자식 속성을 포함 하는 속성을 숨길 수 있습니다.  
  
- 부모 프로젝트가 자식 프로젝트의 일부 측면을 프로그래밍 방식으로 제어 하는 중첩 된 프로젝트가 있는 경우  
  
- 특수 디자이너에서 컨트롤을 사용 하는 경우 개발자에 게 컨트롤의 모든 속성에 대 한 모든 권한을 부여 하지 않으려는 경우  
  
- 개체의 범위를 소유 하 고 있고 속성의 뷰를 제한 하려는 경우  
  
### <a name="to-hide-properties-that-have-child-properties"></a>자식 속성을 포함 하는 속성을 숨기려면  
  
1. `pfDisplay`의 매개 변수를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> 로 설정 `FALSE` 합니다.  
  
2. `pfHide`의 매개 변수를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> 로 설정 `TRUE` 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [속성 표시 그리드](../extensibility/internals/properties-display-grid.md)