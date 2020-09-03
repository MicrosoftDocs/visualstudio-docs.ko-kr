---
title: IManagedAddin 인터페이스
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b436d76164b1744cffe16593149f64d219d04bf1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541130"
---
# <a name="imanagedaddin-interface"></a>IManagedAddin 인터페이스
  IManagedAddin 인터페이스를 구현 하 여 관리 되는 VSTO 추가 기능을 로드 하는 구성 요소를 만듭니다. 이 인터페이스는 2007 Microsoft Office 시스템에서 추가 되었습니다.

## <a name="syntax"></a>Syntax

```csharp
[
    object,
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),
    pointer_default(unique),
    oleautomation
]
interface IManagedAddin : IUnknown
{
    HRESULT Load(
        [in] BSTR bstrManifestURL,
        [in] IDispatch *pdispApplication);
    HRESULT Unload();
};
```

## <a name="methods"></a>메서드
 다음 표에서는 IManagedAddin 인터페이스에 의해 정의 되는 메서드를 보여 줍니다.

|Name|설명|
|----------|-----------------|
|[IManagedAddIn::Load](../vsto/imanagedaddin-load.md)|Microsoft Office 애플리케이션에서 관리되는 VSTO 추가 기능을 로드할 때 호출됩니다.|
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Microsoft Office 애플리케이션에서 관리되는 VSTO 추가 기능을 언로드하기 직전에 호출됩니다.|

## <a name="remarks"></a>설명
 2007 Microsoft Office 시스템에서 시작 하 Microsoft Office 응용 프로그램은 IManagedAddin 인터페이스를 사용 하 여 Office VSTO 추가 기능을 로드 하는 데 도움이 됩니다. VSTO 추가 기능 로더 (*VSTOLoader.dll*) 및를 사용 하는 대신 IManagedAddin 인터페이스를 구현 하 여 관리 되는 vsto 추가 기능에 대 한 사용자 고유의 vsto 추가 기능 로더 및 런타임을 만들 수 있습니다 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . 자세한 내용은 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)을 참조하세요.

## <a name="how-managed-add-ins-are-loaded"></a>관리 되는 추가 기능을 로드 하는 방법
 다음 단계는 애플리케이션을 시작할 때 발생합니다.

1. 애플리케이션에서는 다음 레지스트리 키에서 항목을 검색하여 VSTO 추가 기능을 찾습니다.

    **HKEY_CURRENT_USER \Software\Microsoft\Office \\ *\<application name>* \addins\\**

    이 레지스트리 키의 각 항목은 VSTO 추가 기능의 고유 ID입니다. 일반적으로 VSTO 추가 기능 어셈블리의 이름입니다.

2. 애플리케이션은 각 VSTO 추가 기능에 대한 항목에서 `Manifest` 항목을 찾습니다.

    관리 되는 VSTO 추가 기능은 `Manifest` **HKEY_CURRENT_USER \Software\microsoft\office \\ _\<application name>_ \addins \\ _\<add-in ID>_ **의 항목에 매니페스트의 전체 경로를 저장할 수 있습니다. 매니페스트는 VSTO 추가 기능을 로드하는 데 사용되는 정보를 제공하는 파일(일반적으로 XML 파일)입니다.

3. 애플리케이션에서 `Manifest` 항목을 찾으면 관리되는 VSTO 추가 기능 로더 구성 요소를 로드하려고 합니다. 응용 프로그램은 IManagedAddin 인터페이스를 구현 하는 COM 개체를 만들어이를 수행 합니다.

    는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] VSTO 추가 기능 로더 구성 요소 (*VSTOLoader.dll*)를 포함 하거나 IManagedAddin 인터페이스를 구현 하 여 직접 만들 수 있습니다.

4. 애플리케이션은 [IManagedAddin::Load](../vsto/imanagedaddin-load.md) 메서드를 호출하여 `Manifest` 항목의 값을 전달합니다.

5. [IManagedAddin::Load](../vsto/imanagedaddin-load.md) 메서드는 로드 중인 VSTO 추가 기능을 위한 보안 정책 및 애플리케이션 도메인을 구성하는 등 VSTO 추가 기능을 로드하는 데 필요한 작업을 수행합니다.

   응용 프로그램에서 관리 되는 VSTO 추가 기능을 검색 하 고 로드 하는 데 사용 Microsoft Office 하는 레지스트리 키에 대 한 자세한 내용은 [Vsto 추가 기능에 대 한 레지스트리 항목](../vsto/registry-entries-for-vsto-add-ins.md)을 참조 하세요.

## <a name="guidance-to-implement-imanagedaddin"></a>IManagedAddin 구현 지침
 IManagedAddin을 구현 하는 경우 다음 CLSID를 사용 하 여 구현을 포함 하는 DLL을 등록 해야 합니다.

 99D651D7-5F7C-470E-8A3B-774D5D9536AC

 Microsoft Office 응용 프로그램은이 CLSID를 사용 하 여 IManagedAddin를 구현 하는 COM 개체를 만듭니다.

> [!CAUTION]
> 이 CLSID는의 *VSTOLoader.dll* 에서도 사용 됩니다 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . 따라서 IManagedAddin를 사용 하 여 사용자 고유의 VSTO 추가 기능 로더 및 런타임 구성 요소를 만드는 경우를 사용 하는 VSTO 추가 기능을 실행 하는 컴퓨터에 구성 요소를 배포할 수 없습니다 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="see-also"></a>추가 정보
- [Visual Studio에서 Office 개발을 &#40;관리 되지 않는 API 참조&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)
