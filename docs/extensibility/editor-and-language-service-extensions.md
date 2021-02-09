---
title: 편집기 및 언어 서비스 확장 프로그램 | Microsoft Docs
description: Windows Presentation Foundation를 사용 하 여 구현 되 고 관리 코드로 작성 되는 Visual Studio 코드 편집기의 대부분 기능을 확장할 수 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 038253d1863c2d599c7c7a1e5c5a1398d67740ab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883521"
---
# <a name="editor-and-language-service-extensions"></a>편집기 및 언어 서비스 확장
Visual Studio 코드 편집기의 기능을 대부분 확장할 수 있습니다. 편집기는 Windows Presentation Foundation (WPF)를 기반으로 하며 관리 코드로 작성 됩니다. 이 디자인은 이전 버전의 Visual Studio에 있는 디자인과는 다르지만 대부분의 동일한 기능을 제공 합니다. 편집기를 확장 하려면 MEF (Managed Extensibility Framework)를 사용 합니다.

 Visual Studio SDK는 이전 버전용으로 작성 된 Vspackage를 지원 하기 위해 *shim* 이라는 어댑터를 제공 합니다. 그럼에도 불구 하 고 기존 VSPackage 있는 경우 더 나은 성능과 안정성을 얻기 위해 새 기술로 업데이트 하는 것이 좋습니다.

## <a name="related-topics"></a>관련 항목

|제목|Description|
|-----------|-----------------|
|[편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)|편집기 항목 템플릿을 사용 하는 방법을 소개 합니다.|
|[편집기 및 언어 서비스 확장](../extensibility/extending-the-editor-and-language-services.md)|핵심 편집기의 디자인과 기능을 소개 하 고이를 확장 하는 방법을 보여 주는 문서에 대 한 링크입니다.|
|[편집기의 레거시 인터페이스](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015)|기존 코드에서 핵심 편집기에 액세스 하는 방법을 설명 하는 문서에 대 한 링크입니다.|
|[사용자 지정 편집기 및 디자이너 만들기](../extensibility/creating-custom-editors-and-designers.md)|사용자 지정 편집기를 만드는 방법을 설명 하는 문서에 대 한 링크입니다.|
|[레거시 언어 서비스 확장성](../extensibility/internals/legacy-language-service-extensibility.md)|Visual Studio에 프로그래밍 언어를 통합 하는 방법을 설명 하는 문서에 대 한 링크입니다.|
|[MEF(Managed Extensibility Framework)](/dotnet/framework/mef/index)|MEF (Managed Extensibility Framework)를 소개 합니다.|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Windows Presentation Foundation (WPF)를 소개 합니다.|
