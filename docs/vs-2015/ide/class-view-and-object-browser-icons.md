---
title: 클래스 뷰 및 개체 브라우저 아이콘 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e67763234ff7b3778cccabaed45fbbc0bc04d30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72620478"
---
# <a name="class-view-and-object-browser-icons"></a>클래스 뷰 및 개체 브라우저 아이콘
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

클래스 뷰 * * 및 **개체 브라우저** 는 네임 스페이스, 클래스, 함수 및 변수와 같은 코드 엔터티를 나타내는 아이콘을 표시 합니다. 다음 표에서는 아이콘에 대해 설명합니다.

|아이콘|설명|아이콘|설명|
|----------|-----------------|----------|-----------------|
|![네임스페이스 기호](../ide/media/vxnamespace-icon.gif "vxNamespace_Icon")|네임스페이스|![선언 기호](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|메서드 또는 함수|
|![클래스 아이콘](../ide/media/vxclass-icon.gif "vxClass_Icon")|클래스|![연산자 기호](../ide/media/vxoperator-icon.gif "vxOperator_Icon")|연산자|
|![롤리팝 인터페이스 기호](../ide/media/vxinterface-icon.gif "vxInterface_Icon")|인터페이스|![속성 기호](../ide/media/vxproperty-icon.gif "vxProperty_Icon")|속성|
|![구조체 기호](../ide/media/vxstruct-icon.gif "vxStruct_Icon")|구조체|![필드 아이콘](../ide/media/vxfield-icon.gif "vxField_Icon")|필드 또는 변수|
|![공용 구조체 기호](../ide/media/vxunion-icon.gif "vxUnion_Icon")|Union|![이벤트 기호](../ide/media/vxevent-icon.gif "vxEvent_Icon")|이벤트|
|![열거 기호](../ide/media/vxenum-icon.gif "vxEnum_Icon")|Enum|![상수 아이콘](../ide/media/vxconstant-icon.gif "vxConstant_Icon")|상수|
|![형식 정의 기호](../ide/media/vxtypedef-icon.gif "vxTypeDef_Icon")|TypeDef|![항목 열거 기호](../ide/media/vxenumitem-icon.gif "vxEnumItem_Icon")|항목 열거|
|![Visual Studio 모듈 기호](../ide/media/vxmodule-icon.gif "vxModule_Icon")|Module|![맵 항목 기호](../ide/media/vxmapitem-icon.gif "vxMapItem_Icon")|맵 항목|
|![확장 메서드 기호](../ide/media/extensionmethod.gif "ExtensionMethod")|확장 메서드|![선언 기호](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|외부 선언|
|![대리자 기호](../ide/media/vxdelegate-icon.gif "vxDelegate_Icon")|대리자|![클래스 뷰 및 개체 브라우저의 오류 아이콘](../ide/media/erroricon.gif "ErrorIcon")|Error|
|![예외 기호](../ide/media/vxexception-icon.gif "vxException_Icon")|예외|![템플릿 기호](../ide/media/vxtemplate-icon.gif "vxTemplate_Icon")|템플릿|
|![맵 기호](../ide/media/vxmap-icon.gif "vxMap_Icon")|맵|![오류 느낌표 기호](../ide/media/vxerror-icon.gif "vxError_Icon")|알 수 없음|
|![형식 전달 기호](../ide/media/ob-type-forward.gif "ob_type_forward")|형식 전달|||

## <a name="signal-icons"></a>신호 아이콘
 다음 신호 아이콘은 이전의 모든 아이콘에 적용되며 액세스 가능성을 나타냅니다.

> [!NOTE]
> 프로젝트가 소스 제어 데이터베이스에 포함되어 있는 경우, 추가 신호 아이콘이 표시되어 체크 인 또는 체크 아웃과 같은 소스 제어 상태를 나타낼 수 있습니다.

|아이콘|설명|
|----------|-----------------|
|\<No Signal Icon>|공개. 이 구성 요소 및 참조하는 구성 요소의 모든 곳에서 액세스할 수 있습니다.|
|![신호 Protected 기호](../ide/media/vxsignal-icon-key.gif "vxSignal_Icon_Key")|보호됨. 포함하는 클래스 또는 형식이나, 여기에서 파생된 클래스 또는 형식에서 액세스할 수 있습니다.|
|![신호 Private 기호](../ide/media/vxsignal-icon-lock.gif "vxSignal_Icon_Lock")|비공개. 포함하는 클래스 또는 형식에서만 액세스할 수 있습니다.|
|![신호 Sealed 기호](../ide/media/vxsignal-icon-envelope.gif "vxSignal_Icon_Envelope")|Sealed.|
|![신호 Friend&#47;내부 기호](../ide/media/vxsignal-icon-diamond.gif "vxSignal_Icon_Diamond")|Friend/내부. 프로젝트에서만 액세스할 수 있습니다.|
|![신호 아이콘 화살표](../ide/media/vxsignal-icon-arrow.gif "vxSignal_Icon_Arrow")|바로 가기. 개체에 대한 바로 가기.|

## <a name="see-also"></a>관련 항목
 [코드 구조 보기](../ide/viewing-the-structure-of-code.md)
