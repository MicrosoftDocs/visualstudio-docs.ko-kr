---
title: 편집기에서 Managed Extensibility Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f19b71c86d972b59a9d46f379bf7ec93f63aeb9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679950"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>편집기의 Managed Extensibility Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기는 MEF (Managed Extensibility Framework) 구성 요소를 사용 하 여 빌드됩니다. 사용자 고유의 MEF 구성 요소를 빌드하여 편집기를 확장할 수 있으며 코드에서 편집기 구성 요소도 사용할 수 있습니다.  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>Managed Extensibility Framework 개요  
 MEF는 MEF 프로그래밍 모델을 따르는 응용 프로그램 또는 구성 요소의 기능을 추가 하 고 수정할 수 있도록 하는 .NET 라이브러리입니다. Visual Studio 편집기는 MEF 구성 요소 파트를 제공 하 고 사용할 수 있습니다.  
  
 MEF는 .NET Framework 버전 4 System.ComponentModel.Composition.dll 어셈블리에 포함 되어 있습니다.  
  
 MEF에 대 한 자세한 내용은 [Managed Extensibility Framework (mef)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)를 참조 하세요.  
  
### <a name="component-parts-and-composition-containers"></a>구성 요소 파트 및 컴퍼지션 컨테이너  
 구성 요소 파트는 클래스 또는 클래스의 멤버로, 다음 항목 중 하나 (또는 둘 다)를 수행할 수 있습니다.  
  
- 다른 구성 요소 사용  
  
- 다른 구성 요소에서 사용 해야 합니다.  
  
  예를 들어 웨어하우스 인벤토리 구성 요소에서 제공 하는 제품 가용성 데이터에 따라 달라 지는 주문 항목 구성 요소가 있는 쇼핑 응용 프로그램이 있다고 가정 합니다. MEF 용어로 재고 파트는 제품 가용성 데이터를 *내보낼* 수 있으며 주문 항목 파트는 데이터를 *가져올* 수 있습니다. 주문 항목 부분과 재고 부분은 서로를 알 필요가 없습니다. 호스트 응용 프로그램에서 제공 하는 *컴퍼지션 컨테이너* 는 내보내기 집합을 유지 관리 하 고 내보내기 및 가져오기를 확인 하는 일을 담당 합니다.  
  
  컴퍼지션 컨테이너는 <xref:System.ComponentModel.Composition.Hosting.CompositionContainer> 일반적으로 호스트에서 소유 합니다. 컴퍼지션 컨테이너는 내보낸 구성 요소 파트의 *카탈로그* 를 유지 관리 합니다.  
  
### <a name="exporting-and-importing-component-parts"></a>구성 요소 파트 내보내기 및 가져오기  
 모든 기능은 public 클래스 또는 클래스의 공용 멤버 (속성 또는 메서드)로 구현 된 경우에만 내보낼 수 있습니다. 에서 구성 요소 파트를 파생할 필요는 없습니다 <xref:System.ComponentModel.Composition.Primitives.ComposablePart> . 대신 <xref:System.ComponentModel.Composition.ExportAttribute> 내보내려는 클래스 또는 클래스 멤버에 특성을 추가 해야 합니다. 이 특성은 다른 구성 요소 파트가 기능을 가져올 수 있는 *계약* 을 지정 합니다.  
  
### <a name="the-export-contract"></a>내보내기 계약  
 는 <xref:System.ComponentModel.Composition.ExportAttribute> 내보낼 엔터티 (클래스, 인터페이스 또는 구조체)를 정의 합니다. 일반적으로 export 특성은 내보내기의 유형을 지정 하는 매개 변수를 사용 합니다.  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 기본적으로 특성은 <xref:System.ComponentModel.Composition.ExportAttribute> 내보내기 클래스의 형식인 계약을 정의 합니다.  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 이 예제에서 기본 특성은 `[Export]` 와 동일 `[Export(typeof(TestAdornmentLayerDefinition))]` 합니다.  
  
 다음 예제와 같이 속성이 나 메서드를 내보낼 수도 있습니다.  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>MEF 내보내기 가져오기  
 MEF 내보내기를 사용 하려는 경우 계약 (일반적으로 형식)을 알고 있어야 하 고 해당 값이 있는 특성을 추가 해야 합니다 <xref:System.ComponentModel.Composition.ImportAttribute> . 기본적으로 가져오기 특성은 수정 하는 클래스의 형식인 하나의 매개 변수를 사용 합니다. 다음 코드 줄에서 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> 형식을 가져옵니다.  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>MEF 구성 요소 파트에서 편집기 기능 가져오기  
 기존 코드가 MEF 구성 요소 부분인 경우 MEF 메타 데이터를 사용 하 여 편집기 구성 요소 파트를 사용할 수 있습니다.  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>MEF 구성 요소 파트에서 편집기 기능을 사용 하려면  
  
1. GAC (전역 어셈블리 캐시)에 있는 System.Composition.ComponentModel.dll에 대 한 참조와 편집기 어셈블리에 대 한 참조를 추가 합니다.  
  
2. 관련 using 문을 추가 합니다.  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3. `[Import]`다음과 같이 서비스 인터페이스에 특성을 추가 합니다.  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4. 서비스를 구한 후에는 해당 구성 요소 중 하나를 사용할 수 있습니다.  
  
5. 어셈블리를 컴파일한 후에는.. Visual Studio 설치의 \Common7\IDE\Components\ 폴더입니다.  
  
## <a name="see-also"></a>관련 항목  
 [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
