---
title: MSBuild의 로깅 | Microsoft 문서
description: MSBuild 로깅을 통해 빌드 이벤트, 메시지, 경고 및 오류를 로그 파일에 캡처하여 빌드 진행률을 모니터링할 수 있는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, logging
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: afbb79e2ce8ebdccc68def6ca4c42fde85c11bf0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966255"
---
# <a name="logging-in-msbuild"></a>MSBuild 로그인

로깅은 빌드의 진행률을 모니터링할 수 있는 방법을 제공합니다. 로깅은 빌드 이벤트, 메시지, 경고 및 오류를 로그 파일에 캡처합니다.

## <a name="in-this-section"></a>섹션 내용

- [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md)

 MSBuild에서의 로깅의 다양한 측면에 대해 설명합니다.

- [빌드 로거](../msbuild/build-loggers.md)

 프로세서 로거를 만드는 데 필요한 단계를 간략하게 설명합니다.

- [다중 프로세서 환경에서의 로그인](../msbuild/logging-in-a-multi-processor-environment.md)

 다중 프로세스 환경 및 두 개의 다중 프로세서 로깅 모델에서 로깅이 작동하는 방식에 대해 설명합니다.

- [다중 프로세서 인식 로거 작성](../msbuild/writing-multi-processor-aware-loggers.md)

 다중 프로세서 인식 로거를 만드는 방법 및 ConfigurableForwardingLogger를 사용하는 방법을 간략하게 설명합니다.

- [전달 로거 만들기](../msbuild/creating-forwarding-loggers.md)

 사용자 지정 전달 로거를 만드는 방법을 간략하게 설명합니다.

## <a name="see-also"></a>참고 항목

- [병렬로 여러 프로젝트 빌드](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) 여러 프로젝트를 병렬로 실행하여 더 빠르게 여러 프로젝트를 빌드하는 방법을 설명합니다.
