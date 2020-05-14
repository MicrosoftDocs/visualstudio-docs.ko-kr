---
title: 웹 사이트 지원 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22047ad1b0709cefa200656e61f8e0d39ace94c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703439"
---
# <a name="web-site-support"></a>웹 사이트 지원
웹 사이트 프로젝트 시스템은 웹 프로젝트를 만드는 프로젝트 시스템입니다. 웹 프로젝트는 웹 응용 프로그램을 만듭니다. 웹 사이트 프로젝트는 연결된 코드가 있는 각 웹 페이지에 대해 하나의 실행 파일을 생성합니다. /App_Code 폴더의 소스 코드 파일에서 추가 실행 파일이 생성됩니다.

 웹 사이트 프로젝트 시스템은 기존 프로젝트 시스템에 템플릿 및 등록 특성을 추가하여 만들어집니다. 이러한 특성 중 하나는 언어에 대한 IntelliSense 공급자를 선택합니다. IntelliSense 공급자 구현은 참조를 처리하고 캐시되지 않은 스마트 웹 페이지가 요청될 때 언어 컴파일러를 호출합니다.

 웹 페이지를 컴파일하는 데 사용되는 언어 [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]컴파일러는 에 등록되어야 합니다. Web.config 파일의 [ \<> 요소 컴파일러를](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) 사용하여 다음 예제와 같이 컴파일러를 등록할 수 있습니다.

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>섹션 내용
- [웹 사이트 지원 템플릿](../../extensibility/internals/web-site-support-templates.md)

 새 웹 사이트 프로젝트 및 관련 항목을 만드는 데 사용할 수 있는 템플릿을 나열합니다.

- [웹 사이트 지원 특성](../../extensibility/internals/web-site-support-attributes.md)

 웹 사이트 프로젝트에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 연결하는 등록 특성을 [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]제공합니다.

## <a name="related-sections"></a>관련 단원
- [웹 프로젝트](../../extensibility/internals/web-projects.md)

 웹 프로젝트, 웹 사이트 프로젝트 및 웹 응용 프로그램 프로젝트의 두 가지 종류에 대한 개요를 제공합니다.
