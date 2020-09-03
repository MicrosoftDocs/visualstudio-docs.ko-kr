---
title: 레거시 언어 서비스의 모델 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707043"
---
# <a name="model-of-a-legacy-language-service"></a>레거시 언어 서비스 모델
언어 서비스는 특정 언어의 요소와 기능을 정의 하 고 편집기에 해당 언어에 대 한 정보를 제공 하는 데 사용 됩니다. 예를 들어 편집기는 구문 색 지정을 지원 하기 위해 언어의 요소와 키워드를 알고 있어야 합니다.

 언어 서비스는 편집기 및 편집기를 포함 하는 뷰에 의해 관리 되는 텍스트 버퍼와 긴밀 하 게 작동 합니다. Microsoft IntelliSense **요약 정보** 옵션은 언어 서비스에서 제공 하는 기능의 예입니다.

## <a name="a-minimal-language-service"></a>최소 언어 서비스
 가장 기본적인 언어 서비스는 다음과 같은 두 개체를 포함 합니다.

- *언어 서비스* 는 인터페이스를 구현 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> . 언어 서비스에는 해당 이름, 파일 이름 확장명, 코드 창 관리자 및 svc를 포함 하 여 언어에 대 한 정보가 포함 되어 있습니다.

- *Svc* 는 인터페이스를 구현 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> .

  다음 개념 그리기에서는 기본 언어 서비스의 모델을 보여 줍니다.

  ![언어 서비스 모델 그래픽](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") 기본 언어 서비스 모델

  문서 창은 편집기의 *문서 뷰* (이 경우 핵심 편집기)를 호스팅합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 편집기에서 문서 뷰 및 텍스트 버퍼를 소유 합니다. 이러한 개체 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 는 *코드 창*이라는 특수 문서 창을 통해에서 작동 합니다. 코드 창은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> IDE에서 만들고 제어 하는 개체에 포함 되어 있습니다.

  지정 된 확장명을 가진 파일이 로드 되 면 편집기는 해당 확장과 연결 된 언어 서비스를 찾아 메서드를 호출 하 여 코드 창으로 전달 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> . 언어 서비스는 인터페이스를 구현 하는 *코드 창 관리자*를 반환 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> .

  다음 표에서는 모델의 개체에 대 한 개요를 제공 합니다.

| 구성 요소 | Object | 함수 |
|------------------| - | - |
| 텍스트 버퍼 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | 유니코드 읽기/쓰기 텍스트 스트림입니다. 텍스트에서 다른 인코딩을 사용할 수 있습니다. |
| 코드 창 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | 하나 이상의 텍스트 뷰를 포함 하는 문서 창입니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]가 mdi (다중 문서 인터페이스) 모드에 있으면 코드 창은 mdi 자식입니다. |
| 텍스트 보기 | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | 사용자가 키보드와 마우스를 사용 하 여 텍스트를 탐색 하 고 볼 수 있도록 하는 창입니다. 텍스트 뷰가 사용자에 게 편집기로 표시 됩니다. 일반 편집기 창, 출력 창 및 직접 실행 창에서 텍스트 뷰를 사용할 수 있습니다. 또한 코드 창 내에서 하나 이상의 텍스트 뷰를 구성할 수 있습니다. |
| 텍스트 관리자 | <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>포인터를 가져오는 서비스에서 관리 됩니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> | 앞에서 설명한 모든 구성 요소에서 공유 하는 공통 정보를 유지 관리 하는 구성 요소입니다. |
| 언어 서비스 | 구현 종속 구현할 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | 구문 강조 표시, 문 완성 및 중괄호 일치와 같은 언어별 정보를 편집기에 제공 하는 개체입니다. |

## <a name="see-also"></a>추가 정보
- [사용자 지정 편집기의 문서 데이터 및 문서 보기](../../extensibility/document-data-and-document-view-in-custom-editors.md)
