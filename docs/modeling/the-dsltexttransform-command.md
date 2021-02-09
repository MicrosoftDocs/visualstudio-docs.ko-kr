---
title: DslTextTransform 명령
description: TextTransform.exe를 호출 하 고 공통 옵션을 사용 하 여 실행 하는 스크립트를 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f51d1a5cbefc3c2cf60559075a9c9a299664ed07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924505"
---
# <a name="the-dsltexttransform-command"></a>DslTextTransform 명령
DslTextTransform은 TextTransform.exe를 호출 하 고 공통 옵션을 사용 하 여 실행 하는 스크립트입니다. 프로젝트의 야간 빌드를 자동화 하는 데에는 DslTextTransformation 함께를 사용할 수 있습니다. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 자세한 내용은 [TextTransform 유틸리티를 사용 하 여 파일 생성](../modeling/generating-files-with-the-texttransform-utility.md)을 참조 하세요.

 다음 디렉터리에는 DslTextTransform이 있습니다.

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 다음 인수를 DslTextTransform에 대 한 입력으로 지정할 수 있습니다.

- 도메인 모델 프로젝트의 출력 디렉터리입니다.

- 디자이너 정의 프로젝트의 출력 디렉터리입니다.

- 텍스트 템플릿 파일의 위치입니다.

  DslTextTransform은 기본 지시문 프로세서 및 어셈블리를 사용 하 여 지정 된 텍스트 템플릿 파일을 처리 합니다. 사용자 지정 지시문 프로세서를 만드는 경우 TextTransform.exe를 호출 하는 고유한 배치 파일을 만들 수 있습니다. 이 배치 파일에서 어셈블리 및 연결 된 사용자 지정 지시문 프로세서를 지정할 수 있습니다.
