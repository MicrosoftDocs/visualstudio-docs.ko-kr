---
title: 레거시 언어 서비스 모델 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f024a02641902843f673ce3ff8583a4bce3b135
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707043"
---
# <a name="model-of-a-legacy-language-service"></a>레거시 언어 서비스 모델
언어 서비스는 특정 언어의 요소와 기능을 정의하며 편집자에게 해당 언어와 관련된 정보를 제공하는 데 사용됩니다. 예를 들어, 편집기는 구문 색칠을 지원하기 위해 언어의 요소와 키워드를 알아야 합니다.

 언어 서비스는 편집기에서 관리하는 텍스트 버퍼및 편집기가 포함된 뷰와 긴밀하게 작동합니다. Microsoft IntelliSense **빠른 정보** 옵션은 언어 서비스에서 제공하는 기능의 예입니다.

## <a name="a-minimal-language-service"></a>최소한의 언어 서비스
 가장 기본적인 언어 서비스에는 다음과 같은 두 개체가 포함되어 있습니다.

- *언어 서비스는* 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 구현합니다. 언어 서비스에는 이름, 파일 이름 확장자, 코드 창 관리자 및 색지정법을 비롯한 언어에 대한 정보가 있습니다.

- *착색기는* 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 구현합니다.

  다음 개념 도면은 기본 언어 서비스의 모델을 보여 주며,

  ![언어 서비스 모델 그래픽](../../extensibility/media/vslanguageservicemodel.gif "vs언어 서비스 모델") 기본 언어 서비스 모델

  문서 창은 편집자의 *문서 보기를* 호스트합니다(이 경우 핵심 편집기). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 문서 뷰와 텍스트 버퍼는 편집기에서 소유합니다. 이러한 개체는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] *코드*창이라는 특수 문서 창을 통해 작동합니다. 코드 창은 IDE에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 의해 생성되고 제어되는 개체에 포함되어 있습니다.

  지정된 확장이 있는 파일이 로드되면 편집기는 해당 확장명과 연결된 언어 서비스를 찾고 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> 메서드를 호출하여 코드 창을 전달합니다. 언어 서비스는 인터페이스를 구현하는 코드 창 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> *관리자를*반환합니다.

  다음 표에서는 모델의 개체에 대한 개요를 제공합니다.

| 구성 요소 | Object | 함수 |
|------------------| - | - |
| 텍스트 버퍼 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | 유니코드 읽기/쓰기 텍스트 스트림입니다. 텍스트가 다른 인코딩을 사용할 수 있습니다. |
| 코드 창 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | 하나 이상의 텍스트 뷰가 포함된 문서 창입니다. MDI(다중 문서 인터페이스) 모드에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 있으면 코드 창은 MDI 자식입니다. |
| 텍스트 보기 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | 사용자가 키보드와 마우스를 사용하여 텍스트를 탐색하고 볼 수 있는 창입니다. 텍스트 보기는 사용자에게 편집기로 나타납니다. 일반 편집기 창, 출력 창 및 즉시 창에서 텍스트 보기를 사용할 수 있습니다. 또한 코드 창 내에서 하나 이상의 텍스트 보기를 구성할 수 있습니다. |
| 텍스트 관리자 | <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> 포인터를 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> 가져오는 서비스에서 관리 | 앞서 설명한 모든 구성 요소에서 공유하는 공통 정보를 유지하는 구성 요소입니다. |
| 언어 서비스 | 구현 종속; 구현<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | 구문 강조 표시, 명령문 완성 및 중괄호 일치와 같은 언어 별 정보를 편집기에게 제공하는 개체입니다. |

## <a name="see-also"></a>참조
- [사용자 지정 편집기의 문서 데이터 및 문서 보기](../../extensibility/document-data-and-document-view-in-custom-editors.md)
