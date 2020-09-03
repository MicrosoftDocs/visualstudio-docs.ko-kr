---
title: '방법: Windows에 대 한 자동화 기능 제공 Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fec2b9ef6612a294dc70d129cf4bdd3dde843262
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905264"
---
# <a name="how-to-provide-automation-for-windows"></a>방법: windows에 대 한 자동화 제공

문서 및 도구 창에 대 한 자동화를 제공할 수 있습니다. 자동화를 제공 하는 것은 창에서 자동화 개체를 사용할 수 있도록 하 고 환경에서 작업 목록과 같이 미리 만들어진 자동화 개체를 아직 제공 하지 않을 때마다 사용 하는 것이 좋습니다.

## <a name="automation-for-tool-windows"></a>도구 창에 대 한 자동화

환경에서는 <xref:EnvDTE.Window> 다음 절차에 설명 된 대로 표준 개체를 반환 하 여 도구 창에 대 한 자동화를 제공 합니다.

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>__VSFPROPID를 사용 하 여 환경을 통해 메서드를 호출 [합니다. ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>)개체를 `VSFPROPID` 가져오는 매개 변수로 VSFPROPID_ExtWindowObject `Window` .

2. 호출자가를 통해 도구 창에 대 한 VSPackage automation 개체를 요청 하면 <xref:EnvDTE.Window.Object%2A> 환경에서 `QueryInterface` `IExtensibleObject` , <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> 또는 인터페이스를 호출 합니다 `IDispatch` . `IExtensibleObject`와 `IVsExtensibleObject` 는 모두 메서드를 제공 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> 합니다.

3. 그러면 환경에서 전달 하는 메서드를 호출할 때 `GetAutomationObject` `NULL` VSPackage 관련 개체를 다시 전달 하 여 응답 합니다.

4. `QueryInterface`및에 대 한 호출이 `IExtensibleObject` `IVsExtensibleObject` 실패 하면 환경에서 `QueryInterface` 를 호출 `IDispatch` 합니다.

## <a name="automation-for-document-windows"></a>문서 창에 대 한 자동화

<xref:EnvDTE.Document>편집기는 <xref:EnvDTE.Document> 인터페이스를 구현 하 `IExtensibleObject` 고에 응답 하 여 개체의 고유한 구현을 가질 수 있지만 환경 에서도 표준 개체를 사용할 수 있습니다 `GetAutomationObject` .

또한 편집기는 <xref:EnvDTE.Document.Object%2A> 또는 인터페이스를 구현 하 여 메서드를 통해 검색 되는 VSPackage 특정 자동화 개체를 제공할 수 `IVsExtensibleObject` 있습니다 `IExtensibleObject` . 고가 중 [진한 샘플](https://github.com/Microsoft/VSSDK-Extensibility-Samples) 은 RTF 문서 관련 자동화 개체를 제공 합니다.

## <a name="see-also"></a>참고 항목

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
