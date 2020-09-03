---
title: DisassemblyData | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737277"
---
# <a name="disassemblydata"></a>DisassemblyData
IDE (통합 개발 환경)에서 표시할 하나의 디스어셈블리 명령을 설명 합니다.

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
입력 하는 필드를 지정 하는 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) 상수입니다.

`bstrAddress`\
일부 시작 지점 (일반적으로 연결 된 함수의 시작)의 오프셋 주소입니다.

`bstrCodeBytes`\
이 명령의 코드 바이트입니다.

`bstrOpcode`\
이 명령의 opcode입니다.

`bstrOperands`\
이 명령의 피연산자입니다.

`bstrSymbol`\
주소와 연결 된 기호 이름 (있는 경우)입니다 (public 기호, 레이블 등).

`uCodeLocationId`\
이 디스어셈블 선의 코드 위치 식별자입니다. 한 줄의 코드 컨텍스트 주소가 다른 줄의 코드 컨텍스트 주소 보다 큰 경우 첫 번째의 디스어셈블 된 코드 위치 식별자도 두 번째의 코드 위치 식별자 보다 큽니다.

`posBeg`\
문서에서 디스어셈블리 데이터가 시작 되는 위치에 해당 하는 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 입니다.

`posEnd`\
문서에서 디스어셈블리 데이터가 끝나는 위치에 해당 하는 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 입니다.

`bstrDocumentUrl`\
파일 이름으로 표시할 수 있는 텍스트 문서의 경우 `bstrDocumentUrl` 이 필드는 형식을 사용 하 여 원본을 찾을 수 있는 파일 이름으로 채워집니다 `file://file name` .

파일 이름으로 표현할 수 없는 텍스트 문서의 경우 `bstrDocumentUrl` 은 문서에 대 한 고유 식별자이 고, 디버그 엔진은 [getdocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) 메서드를 구현 해야 합니다.

이 필드에는 체크섬에 대 한 추가 정보가 포함 될 수도 있습니다. 자세한 내용은 설명 부분을 참조 하십시오.

`dwByteOffset`\
명령이 코드 줄의 시작 부분부터의 바이트 수입니다.

`dwFlags`\
활성 플래그를 지정 하는 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) 상수입니다.

## <a name="remarks"></a>설명
각 `DisassemblyData` 구조는 디스어셈블리의 한 가지 지침을 설명 합니다. 이러한 구조체의 배열은 [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 메서드에서 반환 됩니다.

[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 구조는 텍스트 기반 문서 에서만 사용 됩니다. 이 명령에 대 한 소스 코드 범위는 문이나 줄에서 생성 된 첫 번째 명령 (예:)에 대해서만 채워집니다 `dwByteOffset == 0` .

텍스트가 아닌 문서의 경우 코드에서 문서 컨텍스트를 가져올 수 있으며 `bstrDocumentUrl` 필드는 null 값 이어야 합니다. `bstrDocumentUrl`필드가 `bstrDocumentUrl` 이전 배열 요소의 필드와 같으면를 `DisassemblyData` `bstrDocumentUrl` null 값으로 설정 합니다.

필드에 `dwFlags` `DF_DOCUMENT_CHECKSUM` 플래그가 설정 되어 있으면 추가 체크섬 정보는 필드가 가리키는 문자열 뒤에 옵니다 `bstrDocumentUrl` . 특히 null 문자열 종결자 뒤에는 체크섬 알고리즘을 식별 하는 GUID와 체크섬의 바이트 수를 나타내는 4 바이트 값이 차례로 오고 그 뒤에 체크섬 바이트가 나옵니다. 에서이 필드를 인코드 및 디코딩하는 방법에 대 한이 항목의 예제를 참조 하세요 [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

## <a name="example"></a>예
`bstrDocumentUrl`플래그가 설정 된 경우이 필드에는 문자열이 아닌 추가 정보가 포함 될 수 있습니다 `DF_DOCUMENT_CHECKSUM` . 이 인코딩된 문자열을 만들고 읽는 프로세스는에서 간단 [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] 합니다. 그러나에서는 [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] 다른 문제가 있습니다. 관심이 있는 사용자를 위해 다음 예제에서는에서 인코딩된 문자열을 만드는 한 가지 방법과 [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] 에서 인코딩된 문자열을 디코딩하는 한 가지 방법을 보여 줍니다 [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

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

## <a name="see-also"></a>추가 정보
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
