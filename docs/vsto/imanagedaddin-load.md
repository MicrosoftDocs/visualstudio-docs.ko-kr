---
title: IManagedAddIn::Load
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1307d720e005855770ee68659374dbbfae247d65
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541039"
---
# <a name="imanagedaddinload"></a>IManagedAddIn::Load
  관리되는 VSTO 추가 기능이 로드되면 호출됩니다.

## <a name="syntax"></a>구문

```csharp
HRESULT Load([in] BSTR bstrManifestURL,
             [in] IDispatch *pdispApplication);
```

### <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|*bstrManifestURL*|VSTO 추가 기능에 대한 매니페스트의 전체 경로입니다.|
|*pdispApplication*|VSTO 추가 기능을 로드 하는 호스트 응용 프로그램을 나타내는 IDispatch에 대 한 포인터입니다.|

## <a name="return-value"></a>반환 값
 메서드가 성공적으로 완료되었는지 여부를 나타내는 HRESULT 값입니다.

## <a name="remarks"></a>설명
 매니페스트는 VSTO 추가 기능을 로드하는 데 사용되는 정보를 제공하는 파일(일반적으로 XML 파일)입니다. 예를 들어 매니페스트는 VSTO 추가 기능이 로드될 때 인스턴스화할 VSTO 추가 기능 어셈블리 및 진입점 클래스의 위치를 지정할 수 있습니다.

 *BstrManifestURL* 매개 변수는 `Manifest` VSTO 추가 기능에 대 한 **HKEY_CURRENT_USER \software\microsoft\office \\ _\<application name>_ \addins \\ _\<add-in ID>_ ** 레지스트리 키에 있는 항목의 값을 포함 합니다. 자세한 내용은 [IManagedAddin 인터페이스](../vsto/imanagedaddin-interface.md)를 참조 하세요.

 [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) 메서드를 구현하여 로드되는 VSTO 추가 기능을 위한 애플리케이션 도메인 및 보안 정책 구성 등의 작업을 수행합니다.

## <a name="see-also"></a>참고 항목
- [IManagedAddin 인터페이스](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
