---
title: 문자 모양 컨트롤 (소스 제어 VSPackage) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708315"
---
# <a name="glyph-control-source-control-vspackage"></a>문자 모양 컨트롤 (소스 제어 VSPackage)
소스 제어 Vspackage에서 사용할 수 있는 전체 통합의 일부는 소스 제어에서 항목의 상태를 나타내기 위해 고유한 문자 모양을 표시 하는 기능입니다.

## <a name="levels-of-glyph-control"></a>문자 모양 컨트롤의 수준
 상태 문자 모양은 표시 될 때 항목의 현재 상태 (예: **솔루션 탐색기** 또는 **클래스 뷰**)를 나타내는 아이콘입니다. 소스 제어 VSPackage는 두 가지 수준의 문자 모양 컨트롤을 실행할 수 있습니다. 문자 모양의 선택 항목을 IDE에서 제공 되는 미리 정의 된 문자 모양 집합으로 제한 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 하거나 표시할 사용자 지정 문자 집합을 정의할 수 있습니다.

### <a name="default-set-of-glyphs"></a>기본 문자 모양 집합
 **솔루션 탐색기**항목에 연결 된 상태 문자 모양을 확인 하기 위해 프로젝트는를 사용 하 여 소스 제어에서 상태 문자 모양을 요청 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> 합니다. 소스 제어 VSPackage IDE에서 제공 하는 미리 정의 된 문자 모양으로 제한 되는 문자 모양의 선택을 유지할 수 있습니다. 이 경우 VSPackage는 *vsshell*에 정의 된 문자 모양 열거형을 나타내는 값의 배열을 다시 전달 합니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>를 참조하세요. 이는 체크 아웃 된 문자 모양의 자물쇠 및 체크 아웃 된 문자 모양의 확인 표시와 같이 IDE에서 설정 하는 미리 정의 된 문자 집합입니다.

### <a name="custom-set-of-glyphs"></a>사용자 지정 문자 모양 집합
 원본 제어 VSPackage 설치 되 면 고유한 모양과 느낌을 위해 자체 문자 모양을 사용할 수 있습니다. 새 소스 제어 VSPackage 활성 상태 이면 이전 소스 제어 VSPackage 아직 로드 되었지만 비활성 상태인 경우에도 고유한 문자 모양을 사용 하 여 시작할 수 있어야 합니다. 이 모드에서는 소스 제어 VSPackage가 선택 된 것과 일치 하는 모양을 유지 하기 위해 여전히 기존 아이콘을 사용할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 이 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> 서비스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> VSPackage에서 선택적으로 구현할 수 있는 인터페이스 및 IDE에서 요청 하는 인터페이스를 지원 합니다. IDE에서 요청을 만들 때는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 현재 등록 된 소스 제어 VSPackage에서이 인터페이스를 가져오려고 시도 합니다. 인터페이스가 등록 된 VSPackage에 있는 경우 사용자 지정 문자 모양에 대 한 IDE 요청이 성공 합니다. 그렇지 않으면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE는 기본 문자 모양 집합을 사용 합니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>메서드는에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 다양 한 소스 제어 상태를 표시 하는 이미지 목록을 가져오는 데 사용 됩니다. 소스 제어 VSPackage 사용자 지정 문자 모양에 대 한 이미지 목록에 대 한 핸들을 IDE로 반환 합니다. IDE는이 시점에서 이미지 목록의 복사본을 만들고 나중에이를 사용 하 여 표시할 문자 모양을 선택 합니다. 새 인터페이스가 지원 되지 않거나 `IVsSccGlyphs::GetCustomGlyphList` 메서드가을 반환 하는 경우 `E_NOTIMPL` IDE는에서 제공 하는 기본 문자 모양 목록에서 해당 문자 모양을 가져옵니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
