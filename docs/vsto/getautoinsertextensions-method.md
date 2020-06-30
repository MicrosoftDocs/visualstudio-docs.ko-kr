---
title: GetAutoInsertExtensions 메서드
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
ms.openlocfilehash: f5d88af6f24306b7b243359c9797a2cb7e7449bc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543509"
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions 메서드
  디버깅 하는 동안 자동으로 삽입 되는 Office 용 앱에 대 한 정보를 가져옵니다.

 이 메서드는 나중에 사용하도록 예약됩니다.

## <a name="syntax"></a>구문

```csharp
HRESULT GetAutoInsertExtensions(
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames
);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*psaExtensionNames*|Office 용 응용 프로그램의 확장 이름입니다.|

## <a name="return-value"></a>반환 값
 메서드가 성공적으로 완료되었는지 여부를 나타내는 HRESULT 값입니다.

## <a name="remarks"></a>설명
 삽입할 Office 용 각 앱은 **HKEY_CURRENT_USER \software\microsoft\office\wef\developer**의 값에 해당 하는 office 응용 프로그램 확장 이름으로 반환 됩니다. 호스트는 레지스트리에서 이러한 값을 조회 한 다음 자동으로 확장을 삽입 해야 합니다.
