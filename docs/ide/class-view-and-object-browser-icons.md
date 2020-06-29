---
title: 클래스 뷰 및 개체 브라우저 아이콘
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87bce70f83be2af80f93cf9888432257f6139732
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285150"
---
# <a name="class-view-and-object-browser-icons"></a>클래스 뷰 및 개체 브라우저 아이콘

**클래스 뷰** 및 **개체 브라우저**는 코드 엔터티(예: 네임스페이스, 클래스, 함수 및 변수)를 나타내는 아이콘을 표시합니다. 다음 표에서는 아이콘에 대해 설명합니다.

|아이콘|설명|아이콘|설명|
|----------|-----------------|----------|-----------------|
|![네임스페이스 기호](../ide/media/vxnamespace_icon.gif)|네임스페이스|![선언 기호](../ide/media/vxmethod_icon.gif)|메서드 또는 함수|
|![클래스 아이콘](../ide/media/vxclass_icon.gif)|클래스|![연산자 기호](../ide/media/vxoperator_icon.gif)|연산자|
|![롤리팝 인터페이스 기호](../ide/media/vxinterface_icon.gif)|인터페이스|![속성 기호](../ide/media/vxproperty_icon.gif)|속성|
|![구조체 기호](../ide/media/vxstruct_icon.gif)|구조체|![필드 아이콘](../ide/media/vxfield_icon.gif)|필드 또는 변수|
|![공용 구조체 기호](../ide/media/vxunion_icon.gif)|Union|![이벤트 기호](../ide/media/vxevent_icon.gif)|이벤트|
|![열거 기호](../ide/media/vxenum_icon.gif)|Enum|![상수 아이콘](../ide/media/vxconstant_icon.gif)|상수|
|![형식 정의 기호](../ide/media/vxtypedef_icon.gif)|TypeDef|![항목 열거 기호](../ide/media/vxenumitem_icon.gif)|항목 열거|
|![Visual Studio 모듈 기호](../ide/media/vxmodule_icon.gif)|Module|![맵 항목 기호](../ide/media/vxmapitem_icon.gif)|맵 항목|
|![확장 메서드 기호](../ide/media/extensionmethod.gif)|확장 메서드|![선언 기호](../ide/media/vxmethod_icon.gif)|외부 선언|
|![대리자 기호](../ide/media/vxdelegate_icon.gif)|대리자|![클래스 뷰 및 개체 브라우저의 오류 아이콘](../ide/media/erroricon.gif)|Error|
|![예외 기호](../ide/media/vxexception_icon.gif)|예외|![템플릿 기호](../ide/media/vxtemplate_icon.gif)|템플릿|
|![맵 기호](../ide/media/vxmap_icon.gif)|맵|![오류 느낌표 기호](../ide/media/vxerror_icon.gif)|알 수 없음|
|![형식 전달 기호](../ide/media/ob_type_forward.gif)|형식 전달|||

> [!TIP]
> 이 페이지의 아이콘을 가장 잘 보려면 Microsoft Docs 테마가 **밝게**로 설정되어 있는지 확인합니다. 다음 스크린샷에 표시된 것처럼 페이지 왼쪽 아래에 있는 컨트롤에서 이 색 테마를 설정/해제할 수 있습니다.
>
> ![Docs 테마](../ide/media/toggle-docs-color-theme.png "Microsoft Docs 페이지에 대한 색 테마 설정/해제")

## <a name="signal-icons"></a>신호 아이콘

다음 신호 아이콘은 이전의 모든 아이콘에 적용되며 액세스 가능성을 나타냅니다.

|아이콘|설명|
|----------|-----------------|
|\<No Signal Icon>|공개. 이 구성 요소 및 참조하는 구성 요소의 모든 곳에서 액세스할 수 있습니다.|
|![신호 Protected 기호](../ide/media/vxsignal_icon_key.gif)|보호됨. 포함하는 클래스 또는 형식이나, 여기에서 파생된 클래스 또는 형식에서 액세스할 수 있습니다.|
|![신호 Private 기호](../ide/media/vxsignal_icon_lock.gif)|비공개. 포함하는 클래스 또는 형식에서만 액세스할 수 있습니다.|
|![신호 Sealed 기호](../ide/media/vxsignal_icon_envelope.gif)|Sealed.|
|![신호 Friend&#47;내부 기호](../ide/media/vxsignal_icon_diamond.gif)|Friend/내부. 프로젝트에서만 액세스할 수 있습니다.|
|![신호 아이콘 화살표](../ide/media/vxsignal_icon_arrow.gif)|바로 가기. 개체에 대한 바로 가기.|

> [!NOTE]
> 프로젝트가 소스 제어 데이터베이스에 포함되어 있는 경우, 추가 신호 아이콘이 표시되어 체크 인 또는 체크 아웃과 같은 소스 제어 상태를 나타낼 수 있습니다.

## <a name="see-also"></a>참조

- [코드 구조 보기](../ide/viewing-the-structure-of-code.md)
