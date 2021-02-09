---
title: 메시지 클래스의 .ofs 파일에 잘못 된 속성이 있습니다. "
description: .Ofs 파일에 있는 하나 이상의 속성을 선택한 메시지 클래스에 사용할 수 없는 경우 발생 하는 오류를 수정 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b22870cdb038adee84adc0fd7a56c269cb048626
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841919"
---
# <a name="invalid-properties-in-the-ofs-file-for-the-message-class"></a>메시지 클래스의 .ofs 파일에 잘못 된 속성이 있습니다.

  "선택한 메시지 클래스에 대해 하나 이상의 속성이 잘못 되었습니다." 오류는 Outlook에서 디자인 된 양식 영역을 가져올 때 표시 되지만 양식 영역에 있는 하나 이상의 필드가 **새 양식 영역** 마법사의 마지막 페이지에서 선택 하는 메시지 클래스와 호환 되지 않습니다.

예를 들어 **새 양식 영역** 마법사의 마지막 페이지에서 **작업(IPM.Task)** 을 선택할 수 있습니다. 양식 영역에 **회사 주소** 필드가 있는 경우 작업에 회사 주소가 없기 때문에이 오류가 표시 됩니다. 따라서 **회사 주소** 필드는 메시지 클래스와 호환 되지 않습니다 `IPM.Task` .

 **작업 (IPM. 작업)을 (를)** **새 양식 영역** 마법사의 마지막 페이지에 있습니다. 양식 영역에 **회사 주소** 필드가 있는 경우 작업에 회사 주소가 없기 때문에이 오류가 표시 됩니다. 따라서 **회사 주소** 필드는 메시지 클래스와 호환 되지 않습니다 `IPM.Task` .

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

- **새 양식 영역** 마법사의 마지막 페이지에서 양식 영역의 필드와 호환되는 메시지 클래스를 선택합니다.

- Outlook의 폼 디자이너에서 메시지 클래스와 호환 되지 않는 필드를 제거 합니다. **새 양식 영역** 마법사의 마지막 페이지에서 선택 하려는 필드를 제거 합니다.

## <a name="see-also"></a>참고 항목
- [연습: Outlook에서 디자인 한 양식 영역 가져오기](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
