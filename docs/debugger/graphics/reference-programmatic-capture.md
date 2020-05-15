---
title: 참조(프로그래밍 방식 캡처) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a462d22df9768d2ffc8b344933e9f5c1f556575a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62895523"
---
# <a name="reference-programmatic-capture"></a>참조(프로그램 방식 캡처)
그래픽 진단에서는 프로그래밍 방식 캡처 API를 통해 해당 캡처 기능을 프로그래밍 방식으로 제어할 수 있습니다. 이 API를 사용하면 메시지를 전환하여 그래픽 진단 HUD(헤드업 디스플레이)에 추가하고, 그래픽 로그 파일을 초기화하고 만들며, 그래픽 정보를 캡처할 수 있습니다.

## <a name="programmatic-capture-apis"></a>프로그래밍 방식 캡처 API

### <a name="classes"></a>클래스

|이름|설명|
|----------|-----------------|
|[VsgDbg 클래스](vsgdbg-class.md)|그래픽 진단의 앱 내 구성 요소를 프로그래밍 방식으로 제어하는 인터페이스를 나타냅니다.|

### <a name="preprocessor-symbols"></a>전처리기 기호

|이름|설명|
|----------|-----------------|
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|그래픽 로그 파일이 사용자의 임시 파일 디렉터리에 저장되는지 여부를 존재로 정의합니다.|
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|그래픽 로그 파일의 기본 파일 이름을 정의합니다.|
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|`VsgDbg` 클래스의 기본 인스턴스가 제공되는지 여부를 존재로 정의합니다.|

## <a name="related-articles"></a>관련 문서

| 제목 | 설명 |
| - | - |
| [Capturing Graphics Information](capturing-graphics-information.md) | [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 그래픽 진단 도구를 사용하여 렌더링 문제를 진단할 수 있도록 DirectX 기반 앱에서 그래픽 정보를 캡처하는 방법을 보여 줍니다. |
| [개요](overview-of-visual-studio-graphics-diagnostics.md) | 그래픽 진단을 사용하여 DirectX 게임 및 앱의 렌더링 오류를 디버그하는 방법을 보여 줍니다. |
