---
title: 데코레이터의 속성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb837c9b3d465d229f64fac08dac02af8d50f5fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652013"
---
# <a name="properties-of-decorators"></a>데코레이터의 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

데코레이터는 다이어그램의 모양 또는 연결선에 나타날 수 있는 아이콘, 텍스트 또는 확장/축소 갈매기형 수장입니다. 다음 표에서는 세 가지 데코레이터 종류에 대 한 속성을 보여 줍니다. 일부 속성은 shape 데코레이터 또는 connector 데코레이터에만 표시 됩니다.

 자세한 내용은 [도메인별 언어를 정의 하는 방법](../modeling/how-to-define-a-domain-specific-language.md)을 참조 하세요. 이러한 속성을 사용 하는 방법에 대 한 자세한 내용은 [도메인별 언어 사용자 지정 및 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)을 참조 하세요.

## <a name="expandcollapse-decorator"></a>데코레이터 확장/축소

|속성|설명|기본값|
|--------------|-----------------|-------------|
|DisplayName|생성 된 디자이너에 표시 될 데코레이터의 이름입니다.|확장 축소 데코레이터|
|Name|데코레이터의 이름입니다.|ExpandCollapseDecorator|
|참고|이 데코레이터와 연결 된 비공식 메모입니다.|\<none>|
|System.windows.controls.primitives.iscrollinfo.horizontaloffset|데코레이터의 기본 위치를 기준으로 하는 가로 오프셋 (인치)입니다. (도형만 해당)|0|
|VerticalOffset|데코레이터의 기본 위치를 기준으로 하는 세로 오프셋 (인치)입니다. (도형만 해당)|0|
|OffsetFromLine|기본 위치를 기준으로 하는 선의 데코레이터 오프셋 (인치)입니다. (커넥터에만 해당)|0|
|OffsetFromShape|기본 위치를 기준으로 하는 도형의 데코레이터 오프셋 (인치)입니다. (커넥터에만 해당)|0|
|위치|데코레이터의 기본 위치입니다.|SourceTop|

## <a name="icon-decorator"></a>아이콘 데코레이터

|속성|설명|기본값|
|--------------|-----------------|-------------|
|DefaultIcon|표시할 아이콘 또는 이미지 파일의 경로입니다.|\<none>|
|DisplayName|생성 된 디자이너에 표시할 데코레이터의 이름입니다.|아이콘 데코레이터|
|Name|데코레이터의 이름입니다.|{0} 도형의 icondecorator|
|참고|데코레이터와 연결 된 비공식 메모입니다.|\<none>|
|System.windows.controls.primitives.iscrollinfo.horizontaloffset|데코레이터의 기본 위치를 기준으로 하는 가로 오프셋 (인치)입니다. (도형만 해당)|0|
|VerticalOffset|데코레이터의 기본 위치를 기준으로 하는 세로 오프셋 (인치)입니다. (도형만 해당)|0|
|OffsetFromLine|기본 위치를 기준으로 하는 선의 데코레이터 오프셋 (인치)입니다. (커넥터에만 해당)|0|
|OffsetFromShape|기본 위치를 기준으로 하는 도형의 데코레이터 오프셋 (인치)입니다. (커넥터에만 해당)|0|
|위치|데코레이터의 기본 위치입니다.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|속성|설명|기본값|
|--------------|-----------------|-------------|
|DefaultText|표시할 기본 텍스트입니다.|레이블|
|DisplayName|생성 된 디자이너에 표시할 데코레이터의 이름입니다.|레이블|
|FontSize|데코레이터에 표시 되는 텍스트의 글꼴 크기입니다.|8|
|FontStyle|데코레이터에 표시 되는 텍스트의 글꼴 스타일입니다.|주기적|
|Name|데코레이터의 이름입니다.|레이블|
|참고|데코레이터와 연결 된 비공식 메모입니다.|\<none>|
|System.windows.controls.primitives.iscrollinfo.horizontaloffset|데코레이터의 기본 위치를 기준으로 하는 가로 오프셋 (인치)입니다. (도형만 해당)|0|
|VerticalOffset|데코레이터의 기본 위치를 기준으로 하는 세로 오프셋 (인치)입니다. (도형만 해당)|0|
|OffsetFromLine|기본 위치를 기준으로 하는 선의 데코레이터 오프셋 (인치)입니다. (커넥터에만 해당)|0|
|OffsetFromShape|기본 위치를 기준으로 하는 도형의 데코레이터 오프셋 (인치)입니다. (커넥터에만 해당)|0|
|위치|데코레이터의 기본 위치입니다.|TargetBottom|

## <a name="see-also"></a>관련 항목
 [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
