---
title: 웹 사이트 지원 특성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef75f99480145475278357a552f3ac74c0289800
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703491"
---
# <a name="web-site-support-attributes"></a>웹 사이트 지원 특성
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]웹 사이트 프로젝트를 확장하여 웹 프로그래밍 언어에 대한 지원을 제공할 수 있습니다. 언어를 선택할 때 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 새 **웹 사이트** 대화 상자에 프로젝트 템플릿이 표시될 수 있도록 언어가 자체적으로 등록되어야 합니다.

IronPython 스튜디오 샘플에는 웹 사이트 지원이 포함되어 있습니다. 이 샘플에는 IronPython을 새 웹 프로젝트에 대한 코드 뒤에 있는 언어로 등록하는 다음 특성 클래스가 포함되어 있습니다.

## <a name="websiteprojectattribute"></a>웹사이트프로젝트속성
 이 특성은 언어 프로젝트에 배치됩니다. **새 웹 사이트** 대화 상자의 언어 목록에서 웹 프로그래밍 언어 목록에 **언어를** 추가합니다. 예를 들어 다음 코드는 IronPython을 목록에 추가합니다.

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 이 특성은 템플릿 폴더를 가리키는 템플릿 경로도 설정합니다. 템플릿 폴더의 위치에 대한 자세한 내용은 [웹 사이트 지원 템플릿 을](../../extensibility/internals/web-site-support-templates.md)참조하십시오.

## <a name="websiteprojectrelatedfilesattribute"></a>웹사이트프로젝트관련파일속성
 이 특성은 언어 프로젝트에 배치됩니다. 이를 통해 웹 사이트 프로젝트는 **솔루션 탐색기의**다른 파일 형식(기본)에서 한 파일 형식(관련)을 중첩할 수 있습니다.

 예를 들어 다음 코드는 IronPython 코드 뒤에 있는 파일이 .aspx 파일과 관련되어 있음을 지정합니다. IronPython 웹 사이트 솔루션에서 새 .aspx 웹 페이지를 만들면 새 .py 소스 파일이 생성되고 .aspx 페이지의 자식 노드로 나타납니다.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>프로비던스인텔리센스프로바이더속성
 이 특성은 언어 프로젝트 패키지에 배치됩니다. 언어에 대한 IntelliSense 공급자를 선택합니다.

 예를 들어 다음 코드는 언어 서비스를 제공하기 위해 필요에 따라 구현되는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>PythonIntellisenseProvider의 인스턴스를 지정합니다.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 IVsIntellisenseProject 구현은 참조를 처리하고 코드가 있는 웹 페이지가 요청되었지만 캐시되지 않을 때 언어 컴파일러를 호출합니다.

## <a name="see-also"></a>참조
- [웹 사이트 지원](../../extensibility/internals/web-site-support.md)
