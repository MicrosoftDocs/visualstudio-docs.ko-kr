---
title: 디스어셈블리데이터 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dcf3316ba57bbb25ee171cba7e4edc4923fa270
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737277"
---
# <a name="disassemblydata"></a>DisassemblyData
표시할 통합 개발 환경(IDE)에 대한 하나의 분해 명령에 대해 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct tagDisassemblyData {
    DISASSEMBLY_STREAM_FIELDS dwFields;
    BSTR                      bstrAddress;
    BSTR                      bstrAddressOffset;
    BSTR                      bstrCodeBytes;
    BSTR                      bstrOpcode;
    BSTR                      bstrOperands;
    BSTR                      bstrSymbol;
    UINT64                    uCodeLocationId;
    TEXT_POSITION             posBeg;
    TEXT_POSITION             posEnd;
    BSTR                      bstrDocumentUrl;
    DWORD                     dwByteOffset;
    DISASSEMBLY_FLAGS         dwFlags;
} DisassemblyData;
```

```csharp
public struct DisassemblyData { 
    public uint          dwFields;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrCodeBytes;
    public string        bstrOpcode;
    public string        bstrOperands;
    public string        bstrSymbol;
    public ulong         uCodeLocationId;
    public TEXT_POSITION posBeg;
    public TEXT_POSITION posEnd;
    public string        bstrDocumentUrl;
    public uint          dwByteOffset;
    public uint          dwFlags;
};
```

## <a name="members"></a>멤버
`dwFields`\
입력할 필드를 지정하는 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) 상수입니다.

`bstrAddress`\
주소는 일부 시작점(일반적으로 연결된 함수의 시작 부분)에서 오프셋으로 표시됩니다.

`bstrCodeBytes`\
이 명령의 코드 바이트입니다.

`bstrOpcode`\
이 명령의 opcode입니다.

`bstrOperands`\
이 명령의 설명입니다.

`bstrSymbol`\
주소와 연결된 기호 이름(있는 경우)(공용 기호, 레이블 등)입니다.

`uCodeLocationId`\
이 분해된 줄의 코드 위치 식별자입니다. 한 줄의 코드 컨텍스트 주소가 다른 줄의 코드 컨텍스트 주소보다 큰 경우 첫 번째 줄의 분해된 코드 위치 식별자도 두 번째 코드 위치 식별자보다 커집니다.

`posBeg`\
디스어셈블리 데이터가 시작되는 문서의 위치에 해당하는 [TEXT_POSITION.](../../../extensibility/debugger/reference/text-position.md)

`posEnd`\
분해 데이터가 끝나는 문서의 위치에 해당하는 [TEXT_POSITION.](../../../extensibility/debugger/reference/text-position.md)

`bstrDocumentUrl`\
파일 이름으로 나타낼 수 있는 텍스트 `bstrDocumentUrl` 문서의 경우 필드는 형식을 `file://file name`사용하여 소스를 찾을 수 있는 파일 이름으로 채워져 있습니다.

파일 이름으로 나타낼 수 없는 텍스트 `bstrDocumentUrl` 문서의 경우 문서의 고유 식별자이며 디버그 엔진은 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) 메서드를 구현해야 합니다.

이 필드에는 체크섬에 대한 추가 정보도 포함될 수 있습니다. 자세한 내용은 비고를 참조하십시오.

`dwByteOffset`\
명령의 바이트 수는 코드 줄의 시작 부분부터입니다.

`dwFlags`\
활성 플래그를 지정하는 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) 상수입니다.

## <a name="remarks"></a>설명
각 `DisassemblyData` 구조는 분해의 한 명령을 설명합니다. 이러한 구조의 배열은 [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 메서드에서 반환됩니다.

[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 구조는 텍스트 기반 문서에만 사용됩니다. 이 명령의 소스 코드 범위는 명령문 또는 줄에서 생성된 첫 번째 명령(예: .) 동안만 `dwByteOffset == 0`채워져 있습니다.

텍스트가 아닌 문서의 경우 코드에서 문서 컨텍스트를 가져올 수 있으며 `bstrDocumentUrl` 필드는 null 값이어야 합니다. 필드가 `bstrDocumentUrl` 이전 `bstrDocumentUrl` `DisassemblyData` 배열 요소의 필드와 같으면 null `bstrDocumentUrl` 값으로 설정합니다.

`dwFlags` 필드에 플래그가 `DF_DOCUMENT_CHECKSUM` 설정된 경우 추가 체크섬 정보는 `bstrDocumentUrl` 필드가 가리키는 문자열을 따릅니다. 특히 null 문자열 종말 이후에 는 체크섬 알고리즘을 식별하는 GUID가 뒤따르고 체크섬의 바이트 수를 나타내는 4바이트 값이 차례로 체크섬 바이트가 뒤따릅니다. 에서 이 필드를 인코딩하고 디코딩하는 방법에 대한 [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]이 항목의 예제를 참조하십시오.

## <a name="example"></a>예제
`DF_DOCUMENT_CHECKSUM` 플래그가 `bstrDocumentUrl` 설정된 경우 필드에 문자열 이외의 추가 정보가 포함될 수 있습니다. 이 인코딩된 문자열을 만들고 읽는 프로세스는 에서 [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]간단합니다. 그러나, [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]에서, 그것은 또 다른 문제입니다. 궁금한 사람들을 위해 다음 예제에서는 에서 인코딩된 문자열을 [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] 만드는 한 가지 방법과 에서 인코딩된 문자열을 디코딩하는 한 가지 방법을 보여 주며. [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
    class MyClass
    {
        string EncodeData(string documentString,
                          Guid checksumGuid,
                          byte[] checksumData)
        {
            string returnString = documentString;

            if (checksumGuid == null || checksumData == null)
            {
                // Nothing more to do. Just return the string.
                return returnString;
            }

            returnString += '\0'; // separating null value

            // Add checksum GUID to string.
            byte[] guidDataArray  = checksumGuid.ToByteArray();
            int    guidDataLength = guidDataArray.Length;
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);
            for (int i = 0; i < guidDataLength; i++)
            {
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);
            }
            // Copy guid data bytes to string as wide characters.
            // Assumption: sizeof(char) == 2.
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum count (a 32-bit value).
            Int32 checksumCount = checksumData.Length;
            Marshal.StructureToPtr(checksumCount, pBuffer, true);
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum data.
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);
            for (int i = 0; i < checksumCount; i++)
            {
                Marshal.WriteByte(pBuffer, i, checksumData[i]);
            }
            for (int i = 0; i < checksumCount / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }
            Marshal.FreeCoTaskMem(pBuffer);

            return returnString;
        }

        void DecodeData(    string encodedString,
                        out string documentString,
                        out Guid   checksumGuid,
                        out byte[] checksumData)
        {
            documentString = String.Empty;
            checksumGuid = Guid.Empty;
            checksumData = null;

            IntPtr pBuffer = Marshal.StringToBSTR(encodedString);
            if (null != pBuffer)
            {
                int bufferOffset = 0;

                // Parse string out. String is assumed to be Unicode.
                documentString = Marshal.PtrToStringUni(pBuffer);
                bufferOffset += (documentString.Length + 1) * sizeof(char);

                // Parse Guid out.
                // Read guid bytes from buffer and store in temporary
                // buffer that contains only the guid bytes. Then the
                // Marshal.PtrToStructure() can work properly.
                byte[] guidDataArray  = checksumGuid.ToByteArray();
                int    guidDataLength = guidDataArray.Length;
                IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);
                for (int i = 0; i < guidDataLength; i++)
                {
                    Marshal.WriteByte(pGuidBuffer, i,
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
                }
                bufferOffset += guidDataLength;
                checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));
                Marshal.FreeCoTaskMem(pGuidBuffer);

                // Parse out the number of checksum data bytes (always 32-bit value).
                int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);
                bufferOffset += sizeof(Int32);

                // Parse out the checksum data.
                checksumData = new byte[dataCount];
                for (int i = 0; i < dataCount; i++)
                {
                    checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);
                }
            }
        }
    }
}
```

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
