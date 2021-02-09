---
title: GetValidCompatibleFramework 함수
description: GetValidCompatibleFramework API가 Office 인프라를 지 원하는 방법을 알아보고 코드에서 직접 사용할 수 없습니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b089f954c59219461c8e267ee6e88e47015fc794
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860622"
---
# <a name="getvalidcompatibleframework-function"></a>GetValidCompatibleFramework 함수
  이 API는 Office 인프라를 지원 하며 사용자 코드에서 직접 사용 하기 위한 것이 아닙니다.

## <a name="syntax"></a>구문

```csharp
HRESULT WINAPI GetValidCompatibleFramework(
    LPCWSTR lpwszCompatibleFrameworksXML,
    BSTR* pbstrValidFrameworkTag
);
```

### <a name="parameters"></a>매개 변수

|매개 변수|Description|
|---------------|-----------------|
|*lpwszCompatibleFrameworksXML*|사용 하지 마세요.|
|*pbstrValidFrameworkTag*|사용 하지 마세요.|

## <a name="return-value"></a>반환 값
 함수가 성공 하면 **S_OK** 반환 됩니다. 함수가 실패 하면 오류 코드를 반환 합니다.
