---
title: 이데버그디폴티포트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f560a3dabefb0a8dede6520dcd8fd47f609a7780
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732322"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
이 인터페이스는 포트의 서버 및 알림 시설에 액세스하는 몇 가지 방법을 제공합니다.

## <a name="syntax"></a>구문

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 Visual Studio는 프로그램에 액세스하기 위한 디버그 포트를 나타내기 위해 이 인터페이스를 구현합니다. 사용자 지정 포트 공급자는 원격 디버깅을 처리하는 경우에도 이 인터페이스를 구현할 수 있습니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) 인터페이스의 메서드에 대한 인수는 이 인터페이스를 제공합니다. [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 인터페이스에서 [쿼리인터페이스를](/cpp/atl/queryinterface) 호출하면 이 인터페이스도 얻을 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [IDebugPort2에](../../../extensibility/debugger/reference/idebugport2.md)정의된 메서드 외에도 이 인터페이스는 다음 메서드를 구현합니다.

|방법|설명|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|이 포트에서 포트 알림 인터페이스를 가져옵니다.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|이 포트를 호스팅하는 서버에 인터페이스를 가져옵니다.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|이 포트가 로컬 컴퓨터에서 실행되고 있는지 여부를 확인합니다.|

## <a name="remarks"></a>설명
 `IDebugDefaultPort2`"라는 이름은 기본 포트를 나타내지 않으므로 약간 잘못된 것입니다. "IDebugPort3"이라고 할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
