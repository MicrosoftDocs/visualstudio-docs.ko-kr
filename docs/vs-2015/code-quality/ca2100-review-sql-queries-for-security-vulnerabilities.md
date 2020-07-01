---
title: 'CA2100: 보안 취약성에 대 한 SQL 쿼리 검토 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 797c071cdc74c36afeece304bfa4c708d7bf7147
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521214"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: 보안상 취약한 부분이 있는지 SQL 쿼리를 검토하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|범주|Microsoft.Security|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 메서드는 <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> 문자열 인수에서 메서드로 만들어진 문자열을 사용 하 여 속성을 설정 합니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙에서는 문자열 인수에 사용자 입력이 포함된 것으로 가정합니다. 사용자 입력으로부터 만들어진 SQL 명령 문자열은 SQL 삽입 공격에 취약합니다. SQL 삽입 공격에서 악의적인 사용자는 기본 데이터베이스에 대 한 무단 액세스를 손상 시키거나 획득 하려고 할 때 쿼리 디자인을 변경 하는 입력을 제공 합니다. 일반적인 기술에는 SQL 리터럴 문자열 구분 기호인 작은따옴표 또는 아포스트로피 삽입이 포함 됩니다. SQL 주석을 의미 하는 두 개의 대시 새 명령이 뒤에 오는 세미콜론을 지정 합니다. 사용자 입력이 쿼리에 포함 되어야 하는 경우에는 효율성을 위해 나열 된 다음 중 하나를 사용 하 여 공격의 위험을 줄입니다.

- 저장 프로시저를 사용합니다.

- 매개 변수가 있는 명령 문자열을 사용 합니다.

- 명령 문자열을 빌드하기 전에 형식 및 내용에 대 한 사용자 입력의 유효성을 검사 합니다.

  다음 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 형식은 속성을 구현 <xref:System.Data.IDbCommand.CommandText%2A> 하거나 문자열 인수를 사용 하 여 속성을 설정 하는 생성자를 제공 합니다.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> 및 <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> 및 <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> 및 <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- [System.data.sqlserverce. SqlCeCommand] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->)을 (를) 및 [System.data.sqlserverce] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> 및 <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

  형식의 ToString 메서드를 명시적 또는 암시적으로 사용 하 여 쿼리 문자열을 생성할 때이 규칙을 위반 하는 것을 알 수 있습니다. 다음은 예제입니다.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 악의적인 사용자가 ToString () 메서드를 재정의할 수 있으므로 규칙을 위반 했습니다.

 ToString이 암시적으로 사용 되는 경우에도 규칙이 위반 됩니다.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 매개 변수가 있는 쿼리를 사용 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 명령 텍스트에 사용자 입력이 포함 되어 있지 않으면이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 `UnsafeQuery` `SaferQuery` 매개 변수가 있는 명령 문자열을 사용 하 여 규칙을 충족 하는, 및 메서드를 위반 하는 메서드를 보여 줍니다.

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>참고 항목
 [보안 개요](https://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)
