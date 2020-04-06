---
title: 에디터에서 관리되는 확장성 프레임워크 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 888c5206b87079cf9fa91cb68e9801cb3c4f8c1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702871"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>편집기에서 관리되는 확장성 프레임워크
편집기는 관리되는 확장성 프레임워크(MEF) 구성 요소를 사용하여 빌드됩니다. 사용자 고유의 MEF 구성 요소를 빌드하여 편집기를 확장할 수 있으며 코드에서 편집기 구성 요소도 사용할 수 있습니다.

## <a name="overview-of-the-managed-extensibility-framework"></a>관리되는 확장성 프레임워크 개요
 MEF는 MEF 프로그래밍 모델을 따르는 응용 프로그램 또는 구성 요소의 기능을 추가하고 수정할 수 있는 .NET 라이브러리입니다. Visual Studio 편집기는 MEF 구성 요소 부분을 제공하고 사용할 수 있습니다.

 MEF는 .NET 프레임워크 버전 4 *System.ComponentModel.Composition.dll* 어셈블리에 포함되어 있습니다.

 MEF에 대한 자세한 내용은 [MEF(관리되는 확장성 프레임워크)를](/dotnet/framework/mef/index)참조하십시오.

### <a name="component-parts-and-composition-containers"></a>구성 요소 부품 및 컴포지션 컨테이너
 구성 요소 부분은 다음 중 하나(또는 둘 다)를 수행할 수 있는 클래스 또는 클래스의 멤버입니다.

- 다른 구성 요소 사용

- 다른 구성 요소에서 사용

  예를 들어 웨어하우스 재고 구성 요소에서 제공하는 제품 가용성 데이터에 의존하는 주문 입력 구성 요소가 있는 쇼핑 응용 프로그램을 생각해 보십시오. MEF 용어로 재고 부분은 제품 가용성 데이터를 *내보낼* 수 있으며 주문 항목 부분은 데이터를 *가져올* 수 있습니다. 주문 항목 부분과 재고 부분은 서로에 대해 알 필요가 없습니다. *컴포지션 컨테이너(호스트* 응용 프로그램에서 제공)는 내보내기 집합을 유지하고 내보내기 및 가져오기를 해결하는 책임을 집니다.

  컴포지션 컨테이너는 <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>일반적으로 호스트가 소유합니다. 컴포지션 컨테이너는 내보낸 구성 요소 부품의 *카탈로그를* 유지 관리합니다.

### <a name="export-and-import-component-parts"></a>부품 내보내기 및 가져오기
 공용 클래스 또는 클래스(속성 또는 메서드)의 공용 멤버로 구현되는 한 모든 기능을 내보낼 수 있습니다. 에서 구성 요소 부분을 파생할 <xref:System.ComponentModel.Composition.Primitives.ComposablePart>필요가 없습니다. 대신 내보낼 클래스 <xref:System.ComponentModel.Composition.ExportAttribute> 또는 클래스 멤버에 특성을 추가해야 합니다. 이 특성은 다른 구성 요소 부품이 기능을 가져올 수 있는 *계약을* 지정합니다.

### <a name="the-export-contract"></a>수출 계약
 는 <xref:System.ComponentModel.Composition.ExportAttribute> 내보낼 엔터티(클래스, 인터페이스 또는 구조)를 정의합니다. 일반적으로 내보내기 특성은 내보내기 유형을 지정하는 매개 변수를 사용합니다.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 기본적으로 특성은 <xref:System.ComponentModel.Composition.ExportAttribute> 내보내기 클래스의 형식인 계약을 정의합니다.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 이 예제에서 기본 `[Export]` 특성은 `[Export(typeof(TestAdornmentLayerDefinition))]`와 같습니다.

 다음 예제와 같이 속성 또는 메서드를 내보낼 수도 있습니다.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>MEF 내보내기 가져오기
 MEF 내보내기를 사용하려면 계약(일반적으로 내보낸 형식)을 알고 해당 값을 포함하는 특성을 <xref:System.ComponentModel.Composition.ImportAttribute> 추가해야 합니다. 기본적으로 import 특성은 수정하는 클래스의 형식인 하나의 매개 변수를 사용합니다. 다음 코드 줄은 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> 형식을 가져옵니다.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>MEF 구성 요소 부품에서 편집기 기능 얻기
 기존 코드가 MEF 구성 요소 부품인 경우 MEF 메타데이터를 사용하여 편집기 구성 요소 파트를 사용할 수 있습니다.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>MEF 구성 요소 부품의 편집기 기능을 사용하려면

1. 전역 어셈블리 캐시(GAC)에 있는 *System.Composition.ComponentModel.dll*및 편집기 어셈블리에 대한 참조를 추가합니다.

2. 관련 using 지시문을 추가합니다.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. 다음과 `[Import]` 같이 서비스 인터페이스에 특성을 추가합니다.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. 서비스를 얻은 경우 해당 구성 요소 중 하나를 사용할 수 있습니다.

5. 어셈블리를 컴파일한 경우 *.에 넣습니다. \Visual Studio 설치의\* Common7\IDE\구성 요소 폴더입니다.

## <a name="see-also"></a>참조
- [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
