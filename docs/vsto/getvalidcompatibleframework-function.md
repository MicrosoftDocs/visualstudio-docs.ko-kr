---
title: GetValidCompatibleFramework 함수
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2219417fe8ddae3d11d0e624ad12d3de80e290dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520226"
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

|매개 변수|설명|
|---------------|-----------------|
|*lpwszCompatibleFrameworksXML*|사용 하지 마세요.|
|*pbstrValidFrameworkTag*|사용 하지 마세요.|

## <a name="return-value"></a>반환 값
 함수가 성공 하면 **S_OK**반환 됩니다. 함수가 실패 하면 오류 코드를 반환 합니다.
