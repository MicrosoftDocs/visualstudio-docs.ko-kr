---
title: '방법: 매개 변수의 형식 설명자 정의 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0b3ae803576c98a86a45d175af45aa28b3852134
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016850"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>방법: 매개 변수의 형식 설명자 정의
  형식 설명자는 매개 변수의 데이터 형식을 설명하는 속성을 포함합니다. 형식 설명자는 필드, 엔터티 또는 엔터티 컬렉션을 정의할 수 있습니다. 자세한 내용은 [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\))를 참조 하세요.

### <a name="to-define-the-type-descriptor-of-a-parameter"></a>매개 변수의 형식 설명자를 정의하려면

1. **BDC 메서드 세부 정보** 창에서 매개 변수의 형식 설명자를 선택 합니다.

2. 메뉴 모음에서 **보기**, **속성 창**을 선택 합니다.

3. **속성** 창에서 형식 설명자의 속성을 설정 합니다.

     다음 절차에서는 형식 설명자를 필드, 엔터티 또는 엔터티 컬렉션으로 정의하는 방법을 설명합니다.

### <a name="to-define-a-field"></a>필드를 정의하려면

1. **속성** 창에서 형식 설명자의 **이름** 속성을 엔터티를 나타내는 형식 (예: **FirstName**)의 필드 이름으로 설정 합니다.

2. **TypeName** 속성 옆의 목록에서 적절 한 데이터 형식 (예: **Int32**)을 선택 합니다.

     다른 선택적 매개 변수에 대 한 자세한 내용은 [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\))를 참조 하세요.

### <a name="to-define-an-entity"></a>엔터티를 정의하려면

1. **속성** 창에서 **이름** 속성을 엔터티를 설명 하는 이름 (예: **Contact**)으로 설정 합니다.

2. **TypeName** 속성을 엔터티를 나타내는 형식의 정규화 된 이름으로 설정 합니다. 이 형식은 프로젝트의 클래스, 솔루션에서 참조하는 어셈블리에 정의된 형식 또는 BDC 개체 모델에 정의된 형식일 수 있습니다.

    - 프로젝트의 클래스에 대해 **TypeName** 속성 옆의 아래쪽 화살표를 선택 하 고 표시 되는 대화 상자에서 **현재 프로젝트** 탭을 선택한 후 프로젝트에서 클래스를 선택 합니다.

         정규화된 이름에는 클래스의 네임스페이스 및 이름, LOB 시스템의 이름이 차례로 포함됩니다. 다음 예제에서는 **TypeName** 속성 값을 프로젝트의 클래스로 설정 합니다.

         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`

    - 솔루션의 어셈블리에 있는 형식인 경우 정규화된 이름에는 형식 이름, 어셈블리 이름, 버전 번호, 문화권 및 public 키 토큰이 포함됩니다.

         다음 예제에서는 **TypeName** 속성 값을 솔루션에서 참조 하는 어셈블리에 정의 된 형식으로 설정 합니다.

         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

    - BDC 개체 모델에 정의된 형식인 경우 정규화된 이름에는 형식의 네임스페이스 및 이름이 포함됩니다.

         다음 예에서는 **TypeName** 속성 값을 BDC 개체 모델의 형식으로 설정 합니다.

         `Microsoft.BusinessData.Runtime.DynamicType`

3. **BDC 메서드 세부 정보** 창에서 형식 설명자에 대해 표시 되는 목록을 연 다음 **편집**을 선택 합니다.

     **BDC 탐색기** 창이 열립니다.

4. **BDC 탐색기**에서 형식 설명자의 바로 가기 메뉴를 열고 **형식 설명자 추가**를 선택 합니다.

     새 형식 설명자는 엔터티 형식 설명자에 자식으로 추가됩니다. 이 형식 설명자를 필드로 구성합니다.

5. 4단계를 반복하여 엔터티의 각 필드에 대한 자식 형식 설명자를 추가합니다.

### <a name="to-define-a-collection-of-entities"></a>엔터티 컬렉션을 정의하려면

1. **BDC 메서드 세부 정보** 창에서 원하는 매개 변수의 형식 설명자를 선택 합니다.

2. 메뉴 모음에서 **보기**, **속성 창**을 선택 합니다.

3. **속성** 창에서 **이름** 속성을 엔터티를 설명 하는 이름 (예: **연락처**)으로 설정 합니다.

4. **IsCollection** 속성을 **True**로 설정 합니다. 이는 이 형식 설명자가 엔터티 컬렉션임을 나타냅니다.

5. **TypeName** 속성을 인터페이스에 대 한 참조를 포함 하는 문자열 <xref:System.Collections.Generic.IEnumerable%601> 및 엔터티를 나타내는 형식의 정규화 된 이름으로 설정 합니다. 이 형식은 프로젝트의 클래스, 솔루션에서 참조하는 어셈블리에 정의된 형식 또는 BDC 개체 모델에 정의된 형식일 수 있습니다.

   - 프로젝트의 클래스에 대해 **TypeName** 속성 옆의 아래쪽 화살표를 선택 하 고 표시 되는 대화 상자에서 **현재 프로젝트** 탭을 선택한 후 프로젝트에서 클래스를 선택 합니다.

      정규화된 이름에는 클래스의 네임스페이스 및 이름, LOB 시스템의 이름이 차례로 포함됩니다.

      다음 예제에서는 **TypeName** 속성 값을 프로젝트의 클래스 컬렉션으로 설정 합니다.

      `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace. BdcModel1, BdcModel1] '

   - 솔루션의 어셈블리에 있는 형식인 경우 정규화된 이름에는 형식 이름, 어셈블리 이름, 버전 번호, 문화권 및 public 키 토큰이 포함됩니다.

      다음 예제에서는 **TypeName** 속성 값을 솔루션에서 참조 하는 어셈블리의 형식 컬렉션으로 설정 합니다.

      `System.Collections.Generic.IEnumerable`1 [MyNamespace, myAssemblyName, Version = 4.0.0.0, Culture = 중립, PublicKeyToken = b77a5c561934e089] '

   - BDC 개체 모델에 정의된 형식인 경우 정규화된 이름에는 형식의 네임스페이스 및 이름만 포함됩니다.

      다음 예에서는 **TypeName** 속성 값을 BDC 개체 모델에 정의 된 형식의 컬렉션으로 설정 합니다.

      `System.Collections.Generic.IEnumerable`1 [BusinessData. DynamicType] '

6. **BDC 메서드 세부 정보** 창에서 형식 설명자에 대해 표시 되는 목록을 연 다음 **편집**을 선택 합니다.

    **BDC 탐색기** 창이 열립니다.

7. **BDC 탐색기**에서 형식 설명자의 바로 가기 메뉴를 열고 **형식 설명자 추가**를 선택 합니다.

    새 형식 설명자는 컬렉션 형식 설명자에 자식으로 추가됩니다. 이 형식 설명자를 엔터티로 구성합니다.

## <a name="see-also"></a>추가 정보
- [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)
- [방법: 모델에 엔터티 추가](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [방법: 메서드에 매개 변수 추가](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [방법: 메서드 인스턴스 정의](../sharepoint/how-to-define-a-method-instance.md)
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
