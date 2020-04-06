---
title: '방법: Windows용 자동화 제공 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8716fbaa56cdb77063597fd5e07f6e469cc86a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707959"
---
# <a name="how-to-provide-automation-for-windows"></a>방법: 창에 대한 자동화 제공

문서 및 도구 창에 대한 자동화를 제공할 수 있습니다. 창에서 자동화 개체를 사용할 수 있도록 하려는 경우 자동화를 제공하는 것이 바람직하며 환경은 작업 목록과 마찬가지로 이미 준비된 자동화 개체를 제공하지 않습니다.

## <a name="automation-for-tool-windows"></a>공구 창용 자동화

환경은 다음 절차에 설명된 표준 <xref:EnvDTE.Window> 개체를 반환하여 도구 창에서 자동화를 제공합니다.

1. __VSFPROPID <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 환경을 통해 메서드를 호출합니다. [ ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>)개체를 `VSFPROPID` 얻기 위한 매개 변수로 VSFPROPID_ExtWindowObject. `Window`

2. <xref:EnvDTE.Window.Object%2A>호출자가 도구 창에 대해 VSPackage 관련 자동화 개체를 `QueryInterface` 요청하면 환경이 `IExtensibleObject`를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> `IDispatch` 호출합니다. 둘 `IExtensibleObject` `IVsExtensibleObject` 다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> 방법을 제공한다.

3. 그런 다음 환경이 `GetAutomationObject` 메서드 `NULL`전달을 호출하면 VSPackage 관련 개체를 다시 전달하여 응답합니다.

4. `IExtensibleObject` 호출이 `QueryInterface` `IVsExtensibleObject` 실패하고 실패하면 환경이 `IDispatch`을 호출합니다. `QueryInterface`

## <a name="automation-for-document-windows"></a>문서 창에 대한 자동화

에디터는 <xref:EnvDTE.Document> 인터페이스를 <xref:EnvDTE.Document> 구현하고 `IExtensibleObject` 에 응답하여 개체를 자체적으로 구현할 `GetAutomationObject`수 있지만 표준 개체도 환경에서 사용할 수 있습니다.

또한 편집기는 <xref:EnvDTE.Document.Object%2A> `IVsExtensibleObject` 메서드를 통해 검색된 VSPackage 관련 자동화 개체를 또는 `IExtensibleObject` 인터페이스를 구현하여 제공할 수 있습니다. [VSSDK 샘플은](https://github.com/Microsoft/VSSDK-Extensibility-Samples) RTF 문서별 자동화 개체에 기여합니다.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
