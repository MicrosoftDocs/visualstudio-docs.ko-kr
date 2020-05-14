---
title: 아이디버그프로그램노드2:겟호스트네임 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostName
helpviewer_keywords:
- IDebugProgramNode2::GetHostName
ms.assetid: 16aad1ff-ad34-4394-a2e4-5621374a7729
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 028ee16e7b9c5a30effc683494f68b2bd4eb604f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722059"
---
# <a name="idebugprogramnode2gethostname"></a>IDebugProgramNode2::GetHostName
프로그램을 호스팅하는 프로세스의 이름을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetHostName (
    GETHOSTNAME_TYPE dwHostNameType,
    BSTR*            pbstrHostName
);
```

```csharp
int GetHostName (
    enum_GETHOSTNAME_TYPE dwHostNameType,
    out string            pbstrHostName
);
```

## <a name="parameters"></a>매개 변수
`dwHostNameType`\
【인】 반환할 이름의 형식을 지정하는 [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) 열거형의 값입니다.

`pbstrHostName`\
【아웃】 호스팅 프로세스의 이름을 반환합니다.

## <a name="return-value"></a>Return Value
성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="example"></a>예제
다음 예제에서는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) `CProgram` 인터페이스를 노출 하는 간단한 개체에 대 한이 메서드를 구현 하는 방법을 보여 줍니다. 이 예제에서는 `dwHostNameType` 매개 변수를 무시하고 모듈의 파일 경로의 기본 이름에서 가져온 프로그램 이름만 반환합니다.

```cpp
HRESULT CProgram::GetHostName(DWORD dwHostNameType, BSTR* pbstrHostName) {
    // Check for valid argument.
    if (pbstrHostName)
    {
        char szModule[_MAX_PATH];

        // Attempt to assign to szModule the path for the file used
        // to create the calling process.
        if (GetModuleFileName(NULL, szModule, sizeof (szModule)))
        {
            // If successful then declare several char arrays
            char  szDrive[_MAX_DRIVE];
            char  szDir[_MAX_DIR];
            char  szName[_MAX_FNAME];
            char  szExt[_MAX_EXT];
            char  szFilename[_MAX_FNAME + _MAX_EXT];
            WCHAR wszFilename[_MAX_FNAME + _MAX_EXT];

            // Break the szModule path name into components.
            _splitpath(szModule, szDrive, szDir, szName, szExt);

            // Copy the base file name szName into szFilename.
            lstrcpy(szFilename, szName);
            // Append the field extension szExt into szFilename.
            lstrcat(szFilename, szExt);

            // Convert the szFilename sequence of multibyte characters
            // to the wszFilename sequence of wide characters.
            mbstowcs(wszFilename, szFilename, sizeof (wszFilename) / 2);

            // Assign the wszFilename to the value at *pbstrHostName.
            *pbstrHostName = SysAllocString(wszFilename);

            return S_OK;
        }
    }

    return E_INVALIDARG;
}
```

## <a name="see-also"></a>참조
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
