---
title: 글리프 제어 (소스 제어 VS패키지) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9db1b4542eae293e39cda674fac3eb984aa77d3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708315"
---
# <a name="glyph-control-source-control-vspackage"></a>글리프 제어(소스 제어 VSPackage)
소스 제어 VSPackage에 사용할 수 있는 심층 통합의 일부는 소스 제어 하에 있는 항목의 상태를 나타내기 위해 자체 글리프를 표시하는 기능입니다.

## <a name="levels-of-glyph-control"></a>글리프 제어 수준
 상태 문선은 예를 들어 **솔루션 탐색기** 또는 **클래스 보기에서**항목의 현재 상태를 나타내는 아이콘입니다. 소스 제어 VSPackage는 두 가지 수준의 글리프 컨트롤을 행사할 수 있습니다. IDE에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 제공하는 미리 정의된 글리프 집합으로 글리프 선택을 제한하거나 표시할 문말의 사용자 지정 집합을 정의할 수 있습니다.

### <a name="default-set-of-glyphs"></a>글리프의 기본 집합
 **솔루션 탐색기의**항목과 연결된 상태 글리프를 확인하려면 프로젝트가 을 사용하여 소스 컨트롤에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>상태 글리프를 요청합니다. 소스 제어 VSPackage는 IDE에서 제공하는 미리 정의된 글리프로 제한되는 글리프 선택을 유지하도록 결정할 수 있습니다. 이 경우 VSPackage는 *vsshell.idl에*정의된 글리프 열거를 나타내는 값 배열을 다시 전달합니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>을 참조하세요. 이 세트는 IDE에서 설정한 미리 정의된 글리프 집합입니다(예: 체크 인 글리프에 대한 자물쇠 및 체크 아웃된 글리프에 대한 확인 표시).

### <a name="custom-set-of-glyphs"></a>사용자 정의 글리프 세트
 소스 제어 VSPackage는 자체 글리프를 사용하여 설치 시 독특한 모양과 느낌을 만들 수 있습니다. 새 소스 제어 VSPackage가 활성화되어 있으면 이전 소스 제어 VSPackage가 여전히 로드되었지만 비활성 상태인 경우에도 자체 글리프 사용을 시작할 수 있습니다. 이 모드에서소스 컨트롤 VSPackage는 여전히 기존 아이콘을 사용하여 원하는 경우 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 와 일치하는 모양을 유지할 수 있습니다.

 이 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> 서비스는 VSPackage가 선택적으로 구현할 수 있고 IDE에서 요청할 인터페이스를 지원합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> IDE가 요청을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 하면 현재 등록된 소스 제어 VSPackage에서 이 인터페이스를 가져옵니다. 등록된 VSPackage에 인터페이스가 있는 경우 사용자 지정 글리프에 대한 IDE의 요청이 성공합니다. 그렇지 않으면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE는 기본 글리프 집합을 사용합니다.

 이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> 메서드는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 다양한 소스 제어 상태를 보여주는 이미지 목록을 가져오는 데 사용됩니다. 소스 제어 VSPackage는 사용자 지정 글리프에 대한 이미지 목록의 핸들을 IDE로 반환합니다. IDE는 이 시점에서 이미지 목록의 복사본을 만들고 나중에 표시할 글리프를 선택합니다. 새 인터페이스가 지원되지 않거나 `IVsSccGlyphs::GetCustomGlyphList` 메서드가 반환되는 `E_NOTIMPL`경우 IDE는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에서 제공하는 글리프의 기본 목록에서 해당 글리프를 가져옵니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
