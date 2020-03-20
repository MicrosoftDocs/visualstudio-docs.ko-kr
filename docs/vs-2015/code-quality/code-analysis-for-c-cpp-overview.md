---
title: C/C++용 코드 분석 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
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
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 1ce41cd1c0dabc94658b83aa5e2bcdc08d005fdb
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77275363"
---
# <a name="code-analysis-for-cc-overview"></a>C/C++용 코드 분석 개요
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C/C++ 코드 분석 도구는 C/C++ 소스 코드에서 발생할 수 있는 오류에 대한 정보를 개발자에게 제공합니다. 이 도구를 통해 보고되는 일반적인 코딩 오류에는 버퍼 오버런, 초기화되지 않은 메모리, null 포인터 역참조, 메모리 및 리소스 누수 등이 포함됩니다.  
  
## <a name="ide-integrated-development-environment-integration"></a>IDE(통합 개발 환경) 통합  
 개발자가 분석 도구를 자연스럽게 사용할 수 있도록 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 내에 분석 도구가 완전히 통합되었습니다. 빌드 프로세스 중 소스 코드에 대해 생성된 모든 경고가 오류 목록에 표시됩니다. 경고를 유발한 소스 코드로 이동할 수 있으며, 문제의 원인과 가능한 해결책에 대한 추가 정보를 볼 수 있습니다.  
  
## <a name="pragma-support"></a>#pragma 지원  
 개발자는 `#pragma` 지시문을 사용하여 경고를 오류로 처리하고, 경고를 설정 또는 해제하고, 개별 코드 줄에 대한 경고를 표시하지 않을 수 있습니다. 자세한 내용은 [방법: 특정 C/C++ 경고에 대한 코드 분석 설정 및 해제](https://msdn.microsoft.com/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>주석 지원  
 주석은 코드 분석의 정확도를 개선합니다. 주석은 함수 매개 변수 및 반환 형식의 사전 및 사후 조건에 대한 추가 정보를 제공합니다. 자세한 내용은 [방법: _analysis_assume을 사용하여 추가 코드 정보 지정](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>체크 인 정책의 일부로 분석 도구 실행  
 모든 소스 코드 체크 인이 특정 정책에 따라 수행되도록 하는 것이 좋습니다. 특히 해당 분석이 가장 최근의 로컬 빌드 단계로 실행되었는지 확인하는 것이 좋습니다. 코드 분석 체크 인 정책을 사용하도록 설정하는 방법에 대한 자세한 내용은 [코드 분석 체크 인 정책 만들기 및 사용](../code-quality/creating-and-using-code-analysis-check-in-policies.md)을 참조하세요.  
  
## <a name="team-build-integration"></a>팀 빌드 통합  
 빌드 시스템의 통합된 기능을 사용하여 빌드 프로세스의 [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] 단계로 코드 분석 도구를 실행할 수 있습니다. 자세한 내용은 [애플리케이션 빌드](/azure/devops/pipelines/index)를 참조하세요.  
  
## <a name="command-line-support"></a>명령줄 지원  
 다음 예에 나와 있는 것처럼 개발자는 개발 환경 내에 완전히 통합된 기능 외에 명령줄에서도 분석 도구를 사용할 수 있습니다.  
  
 `C:\>cl /analyze Sample.cpp`
