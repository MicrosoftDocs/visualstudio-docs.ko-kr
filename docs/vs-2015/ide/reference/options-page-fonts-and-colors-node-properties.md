---
title: 옵션 페이지, 글꼴 및 색 노드 속성 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23aa4eff3339ad3cd3ab7d4106745dc6fa83df34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662421"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>옵션 페이지, 글꼴 및 색 노드 속성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 문서에서는 **옵션** 대화 상자의 **환경** 범주에 있는 **글꼴 및 색** 범주 아래에 표시되도록 등록된 도구 창의 글꼴 및 색 속성을 설명합니다. 이는 VSPackage가 설치 또는 제거될 경우 변경할 수 있는 색 항목 그룹의 동적 특성을 지원합니다.

 다음 섹션에서는 등록된 창 형식의 예제와 각 창에 사용할 수 있는 속성을 보여 줍니다.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>텍스트 편집기 또는 프린터 또는 대화 상자 및 도구 창
 `DTE.Properties("FontsAndColors", "TextEditor")`

 또는

 `DTE.Properties("FontsAndColors", "Printer")`

 또는

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|FontFamily|Get/Set(문자열)|사용할 글꼴 이름(예: "Courier New").|
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|사용할 문자 집합의 형식을 지정하는 <xref:EnvDTE.vsFontCharSet> 값(예: 히브리어 또는 러시아어)입니다.|
|FontSize|Get/Set(Short)|사용할 글꼴 크기(포인트). 예: 10 또는 12.|

## <a name="see-also"></a>관련 항목
 옵션 [설정 제어](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) 옵션 페이지 옵션 페이지에서 [속성 항목의 이름 결정](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) [페이지, 환경 노드 속성](../../ide/reference/options-page-environment-node-properties.md) [옵션 페이지, 텍스트 편집기 노드 속성](../../ide/reference/options-page-text-editor-node-properties.md)
