---
title: 코딩된 UI 테스트 및 작업 기록 확장
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 05ccb885c799bf2bfd2e3868b80226eca726cc31
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589554"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>코딩된 UI 테스트 및 작업 기록 확장

코딩된 UI 테스트 및 작업 기록에 대한 테스트 프레임워크는 가능한 사용자 인터페이스를 일부 지원하지 않습니다. 테스트하려는 특정 UI를 지원하지 않을 수 있습니다. 예를 들어 Microsoft Excel 스프레드시트에 대한 작업 기록 또는 코딩된 UI 테스트는 바로 만들 수 없습니다. 그러나 코딩된 UI 테스트 프레임워크의 확장성을 이용하여 특정 UI를 지원하는 코딩된 UI 테스트 프레임워크에 대한 고유한 확장을 만들 수 있습니다.

![UI 테스트 아키텍처](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Microsoft Excel을 테스트하기 위한 샘플 확장

이 [블로그 게시물](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/3-introducing-sample-excel-extension/)에는 코딩된 UI 테스트 프레임워크용 [샘플 확장](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip)에 대한 링크가 포함되어 있습니다. 전체 [코딩된 UI 테스트 확장성에 대한 블로그 게시물 시리즈](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/series-on-coded-ui-test-extensibility/)를 볼 수도 있습니다.

> [!NOTE]
> 샘플은 Microsoft Excel 2010에서 사용하도록 제공됩니다. 다른 버전의 Excel에서 작동하거나 작동하지 않을 수 있습니다.

## <a name="see-also"></a>참고 항목

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [UI 자동화를 사용하여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)
- [코딩된 UI 테스트에 대한 모범 사례](../test/best-practices-for-coded-ui-tests.md)
- [코딩된 UI 테스트 및 작업 기록에 지원되는 구성 및 플랫폼](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
