---
title: C/C++용 코드 분석 개요
ms.date: 04/28/2018
ms.topic: conceptual
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 515b9b7eb1b1a4d2dbee6329be782386b8370338
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806315"
---
# <a name="code-analysis-for-cc-overview"></a>C/C++용 코드 분석 개요

C/C++ 코드 분석 도구는 c/C++ 소스 코드에서 가능한 오류에 대 한 정보를 제공 합니다. 이 도구를 통해 보고되는 일반적인 코딩 오류에는 버퍼 오버런, 초기화되지 않은 메모리, null 포인터 역참조, 메모리 및 리소스 누수 등이 포함됩니다. 이 도구는 [ C++ 핵심 지침](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)에 대해 검사를 실행할 수도 있습니다.

## <a name="ide-integrated-development-environment-integration"></a>IDE (통합 개발 환경) 통합

코드 분석 도구는 Visual Studio IDE 내에서 완벽 하 게 통합 됩니다.

빌드 프로세스 중 소스 코드에 대해 생성된 모든 경고가 오류 목록에 표시됩니다. 경고를 유발한 소스 코드로 이동할 수 있으며, 문제의 원인과 가능한 해결책에 대한 추가 정보를 볼 수 있습니다.

## <a name="command-line-support"></a>명령줄 지원

다음 예제와 같이 명령줄에서 분석 도구를 사용할 수도 있습니다.

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 버전 15.7 이상:** CMake를 비롯 한 모든 빌드 시스템을 사용 하 여 명령줄에서 도구를 실행할 수 있습니다.

## <a name="pragma-support"></a>지원 #pragma

`#pragma` 지시어를 사용 하 여 경고를 오류로 처리할 수 있습니다. 경고를 사용 하거나 사용 하지 않도록 설정 하 고 개별 코드 줄에 대 한 경고를 표시 하지 않습니다. 자세한 내용은 [Pragma 지시문 및 __Pragma 키워드](/cpp/preprocessor/pragma-directives-and-the-pragma-keyword)를 참조하세요.

## <a name="annotation-support"></a>주석 지원

주석은 코드 분석의 정확도를 개선합니다. 주석은 함수 매개 변수 및 반환 형식의 사전 및 사후 조건에 대한 추가 정보를 제공합니다. 자세한 내용은 [SAL 주석을 사용 하 여 C/C++ 코드 오류 줄이기](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)를 참조 하세요.

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>체크 인 정책의 일부로 분석 도구 실행

모든 소스 코드 체크 인이 특정 정책에 따라 수행되도록 하는 것이 좋습니다. 특히 해당 분석이 가장 최근의 로컬 빌드 단계로 실행되었는지 확인하는 것이 좋습니다. 코드 분석 체크 인 정책을 사용 하는 방법에 대 한 자세한 내용은 [코드 분석 체크 인 정책 만들기 및 사용](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)을 참조 하세요.

## <a name="team-build-integration"></a>팀 빌드 통합

빌드 시스템의 통합된 기능을 사용하여 빌드 프로세스의 [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] 단계로 코드 분석 도구를 실행할 수 있습니다. 자세한 내용은 [Azure Pipelines](/azure/devops/pipelines/index?view=vsts)를 참조하세요.

## <a name="see-also"></a>참조

- [빠른 시작: C/에 대 한 코드 분석C++](quick-start-code-analysis-for-c-cpp.md)
- [연습: 오류에 대C++ 한 C/코드 분석](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [C/C++용 코드 분석 경고](code-analysis-for-c-cpp-warnings.md)
- [C++ Core Guidelines 검사기 사용](using-the-cpp-core-guidelines-checkers.md)
- [규칙 집합을 사용하여 실행할 C++ 규칙 지정](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [코드 분석 도구를 사용 하 여 드라이버 품질 분석](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [드라이버에 대 한 코드 분석 경고](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
