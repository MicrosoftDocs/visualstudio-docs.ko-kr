---
title: 도메인별 언어에서 코드 생성
description: Domain-Specific 언어 도구가 모델에 표시 된 데이터에서 코드, 문서 및 기타 아티팩트를 생성 하는 강력한 방법을 제공 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58a2537f2c2cab0123bc90e8d0e32a8da89874f6
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362199"
---
# <a name="generating-code-from-a-domain-specific-language"></a>도메인별 언어에서 코드 생성

Microsoft는 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 모델에 표시 된 데이터에서 코드, 문서, 구성 파일 및 기타 아티팩트를 생성 하는 강력한 방법을 제공 합니다. 를 사용 하 여 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 데이터를 나타내는 클래스 집합을 만들 수 있으며, 이름 및 속성이 해당 데이터를 반영 하는 클래스에서 텍스트 템플릿을 작성할 수 있습니다.

예를 들어 Fabrikam에는 고객 이름 및 전자 메일 주소의 XML 파일이 있습니다. 개발자는 고객이 클래스 이며 속성 이름 및 전자 메일을 사용 하는 모델을 만듭니다. 모든 고객의 테이블을 HTML 페이지의 일부로 생성 하는이 조각을 포함 하 여 데이터를 처리 하는 여러 텍스트 템플릿을 작성 합니다.

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

고객 데이터베이스를 처리 하면 XML 파일이 모델 저장소로 읽혀집니다. 를 사용 하 여 만든 *지시문 프로세서* 를 사용 하면 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Customer 클래스를 텍스트 템플릿의 코드에서 사용할 수 있습니다. 동일한 저장소에 대해 많은 텍스트 템플릿을 실행할 수 있습니다.

텍스트 템플릿은에 필수적 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 입니다. 이러한 도구는 도구를 Visual Studio와 통합 하는 데 사용 되는 VSPackage 및 컨트롤 뿐만 아니라 도메인 모델의 요소에 대 한 소스 코드를 생성 하는 데 사용 됩니다.

이 섹션에서는에서 사용 되는 텍스트 템플릿을 만들고 수정 하 고 디버깅 하는 몇 가지 방법에 대해 설명 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 합니다.

## <a name="in-this-section"></a>섹션 내용

[텍스트 템플릿에서 모델에 액세스](../modeling/accessing-models-from-text-templates.md)\
텍스트 템플릿의 도메인별 언어를 참조 하는 방법에 대 한 기본 정보를 제공 합니다.

[연습: 모델에 액세스 하는 텍스트 템플릿 디버그](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)\
도메인 특정 언어를 참조 하는 텍스트 템플릿에서 문제 해결 및 디버깅을 수행 하는 방법을 설명 합니다.

[연습: 생성 된 지시문 프로세서에 호스트 연결](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)\
사용자 지정 호스트를 생성 된 지시문 프로세서에 연결 하는 방법을 설명 합니다.

[DslTextTransform 명령](../modeling/the-dsltexttransform-command.md)\
도메인 특정 언어를 참조 하는 텍스트 템플릿에 대해 명령줄에서 TextTransform 실행 파일을 실행 하는 명령 파일에 대해 설명 합니다.

## <a name="reference"></a>참조

[T4 텍스트 템플릿 작성](../modeling/writing-a-t4-text-template.md)\
텍스트 템플릿 지시문 및 제어 블록의 구문을 제공 합니다.

## <a name="related-sections"></a>관련 단원

[T4 텍스트 템플릿을 사용 하 여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)\
텍스트 템플릿 변환 프로세스에 대해 설명 합니다.

[빌드 프로세스의 코드 생성](../modeling/code-generation-in-a-build-process.md)\
빌드 서버의 DSL에서 파일을 생성 하는 경우이 항목을 읽습니다.
