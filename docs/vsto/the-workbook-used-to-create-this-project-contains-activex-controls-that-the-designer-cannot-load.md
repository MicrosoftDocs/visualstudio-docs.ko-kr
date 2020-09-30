---
title: 통합 문서에 로드할 수 없는 ActiveX 컨트롤이 포함 되어 있습니다.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: error-reference
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 09182fb354ad3ae8937b66952a0acd376d54fe0a
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584453"
---
# <a name="the-workbook-contains-activex-controls-that-cannot-be-loaded"></a>통합 문서에 로드할 수 없는 ActiveX 컨트롤이 포함 되어 있습니다.

  Word 문서 또는 Excel 워크시트에 프로그래밍 방식으로 컨트롤을 추가 하 고 문서 또는 통합 문서를 저장 한 다음 문서 또는 통합 문서를 기반으로 새 문서 수준 솔루션을 만들 때 "이 프로젝트를 만드는 데 사용 된 통합 문서에 디자이너에서 로드할 수 없는 ActiveX 컨트롤이 있습니다." 오류가 표시 됩니다.

 컨트롤의 관리되는 형식을 설명하는 정보는 문서 또는 통합 문서와 함께 저장되지 않습니다. 해당 문서 또는 통합 문서를 기반으로 새 솔루션을 만들 때 Visual Studio에는 호스트 항목 디자이너에 컨트롤을 로드할 충분한 정보가 없습니다.

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. 문서 또는 통합 문서를 엽니다.

2. 런타임에 추가된 컨트롤을 제거합니다. 이렇게 하려면 문서 또는 통합 문서에서 해당 항목을 선택 하 고 **Delete** 키를 누릅니다.

3. 문서 또는 통합 문서를 기반으로 문서 수준 솔루션을 만듭니다.

## <a name="see-also"></a>참고 항목
- [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)
