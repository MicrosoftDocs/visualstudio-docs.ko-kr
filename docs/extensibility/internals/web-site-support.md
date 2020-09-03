---
title: 웹 사이트 지원 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703439"
---
# <a name="web-site-support"></a>웹 사이트 지원
웹 사이트 프로젝트 시스템은 웹 프로젝트를 만드는 프로젝트 시스템입니다. 웹 프로젝트를 사용 하 여 웹 응용 프로그램을 만듭니다. 웹 사이트 프로젝트는 연결 된 코드를 포함 하는 각 웹 페이지에 대해 하나의 실행 파일을 생성 합니다. /App_Code 폴더의 소스 코드 파일에서 추가 실행 파일을 생성 합니다.

 웹 사이트 프로젝트 시스템은 기존 프로젝트 시스템에 템플릿 및 등록 특성을 추가 하 여 만들어집니다. 이러한 특성 중 하나는 언어에 대 한 IntelliSense 공급자를 선택 합니다. 캐시 되지 않은 스마트 웹 페이지가 요청 되 면 IntelliSense 공급자 구현에서 참조를 처리 하 고 언어 컴파일러를 호출 합니다.

 웹 페이지를 컴파일하는 데 사용 되는 언어 컴파일러를에 등록 해야 합니다 [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] . 다음 예제와 같이 Web.config 파일의 [ \<compiler> 요소](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) 를 사용 하 여 컴파일러를 등록할 수 있습니다.

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>섹션 내용
- [웹 사이트 지원 템플릿](../../extensibility/internals/web-site-support-templates.md)

 새 웹 사이트 프로젝트 및 연결 된 항목을 만드는 데 사용할 수 있는 템플릿을 나열 합니다.

- [웹 사이트 지원 특성](../../extensibility/internals/web-site-support-attributes.md)

 웹 사이트 프로젝트를 및에 연결 하는 등록 특성을 표시 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] .

## <a name="related-sections"></a>관련 섹션
- [웹 프로젝트](../../extensibility/internals/web-projects.md)

 두 종류의 웹 프로젝트, 웹 사이트 프로젝트 및 웹 응용 프로그램 프로젝트에 대 한 개요를 제공 합니다.
