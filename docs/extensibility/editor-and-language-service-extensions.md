---
title: 편집자 및 언어 서비스 확장 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e37165dc5fe9ac010545304218e807d923b424b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712028"
---
# <a name="editor-and-language-service-extensions"></a>편집기 및 언어 서비스 확장
Visual Studio 코드 편집기의 대부분의 기능을 확장할 수 있습니다. 편집기는 WPF(Windows 프레젠테이션 재단)를 기반으로 하며 관리 코드로 작성됩니다. 이 디자인은 이전 버전의 Visual Studio의 디자인과 다르지만 대부분의 동일한 기능을 제공합니다. 편집기를 확장하려면 MEF(관리되는 확장성 프레임워크)를 사용합니다.

 Visual Studio SDK는 이전 버전용으로 작성된 VSPackage를 지원하기 위해 *shims로* 알려진 어댑터를 제공합니다. 그럼에도 불구하고 기존 VSPackage가 있는 경우 더 나은 성능과 안정성을 얻으려면 새 기술로 업데이트하는 것이 좋습니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[편집기 항목 템플릿으로 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)|편집기 항목 템플릿 사용에 대한 소개입니다.|
|[편집기 및 언어 서비스 확장](../extensibility/extending-the-editor-and-language-services.md)|핵심 편집기의 디자인과 기능을 소개하고 확장하는 방법을 보여 주는 문서에 대한 링크입니다.|
|[편집기의 레거시 인터페이스](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)|기존 코드에서 핵심 편집기에 액세스하는 방법을 설명하는 문서에 대한 링크입니다.|
|[사용자 지정 편집기 및 디자이너 만들기](../extensibility/creating-custom-editors-and-designers.md)|사용자 지정 편집기를 만드는 방법을 설명하는 문서에 대한 링크입니다.|
|[레거시 언어 서비스 확장성](../extensibility/internals/legacy-language-service-extensibility.md)|프로그래밍 언어를 Visual Studio에 통합하는 방법을 설명하는 문서에 대한 링크입니다.|
|[MEF(Managed Extensibility Framework)](/dotnet/framework/mef/index)|관리되는 확장성 프레임워크(MEF)를 소개합니다.|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|WPF(Windows 프레젠테이션 파운데이션)를 소개합니다.|
