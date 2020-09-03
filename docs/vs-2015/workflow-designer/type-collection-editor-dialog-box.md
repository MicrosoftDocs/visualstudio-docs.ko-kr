---
title: 형식 컬렉션 편집기 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dae99166b8b811df75f2e2777d176e6778b60c7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670152"
---
# <a name="type-collection-editor-dialog-box"></a>형식 컬렉션 편집기 대화 상자
**형식 컬렉션 편집기** 대화 상자는 **보내기** 및 **받기** 작업에 알려진 형식을 추가 하는 데 사용 됩니다. 이 대화 상자는 **InvokeMethod** 활동에 제네릭 형식 인수를 추가 하는 데도 사용 됩니다. **보내기** 및 **받기** 작업에서 알려진 형식을 추가 하는 데 사용 하는 경우 **형식 컬렉션 편집기** 대화 상자에서 고유한 형식을 추가 해야 합니다. 중복 형식을 추가 하 고 **확인**을 클릭 하 여 변경 내용을 커밋하는 경우 오류 메시지가 반환 됩니다. **InvokeMethod** 활동을 사용 하 여 제네릭 형식 인수를 추가 하는 경우 **형식 컬렉션 편집기** 대화 상자를 사용 하 여 중복 된 형식을 추가할 수 있습니다.

> [!NOTE]
> [!INCLUDE[crabout](../includes/crabout-md.md)] 는 [Data Contract Known Types](https://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337)가 포함되어 있습니다.

 다음 표에서는 **형식 컬렉션** 대화 상자의 UI (사용자 인터페이스) 요소에 대해 설명 합니다.

|UI 요소|설명|
|----------------|-----------------|
|**Type List**|추가 또는 제거된 형식의 목록입니다.|

## <a name="to-bring-up-the-type-collection-editor"></a>형식 컬렉션 편집기를 표시하려면

#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Send 및 Receive 활동에 대해 형식 컬렉션 편집기를 표시하려면

1. 디자인 뷰에서 **보내기** 또는 **받기** 작업을 선택 합니다.

2. **F4** 키를 눌러 **속성** 창을 표시 합니다.

3. **속성** 창에서 **knowntypes** 속성 옆에 있는 줄임표 단추를 클릭 합니다.

#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>InvokeMethod 활동에 대해 형식 컬렉션 편집기를 표시하려면

1. 디자인 뷰에서 **InvokeMethod** 활동을 선택 합니다.

2. **F4** 키를 눌러 **속성** 창을 표시 합니다.

3. **속성** 창에서 **GenericTypeArguments** 속성 옆에 있는 줄임표 단추를 클릭 합니다.