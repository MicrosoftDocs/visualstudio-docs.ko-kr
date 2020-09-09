---
title: 보안 경고
ms.date: 10/02/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.securityrules
helpviewer_keywords:
- security [Visual Studio ALM], Enterprise Templates
- security warnings
- managed code analysis warnings, security warnings
- warnings, security
ms.assetid: 60d4e8ea-230a-494f-aa6a-b91db77540e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a40273c3230854e4b1d1a11a3fd02de54d5df745
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89599968"
---
# <a name="security-warnings"></a>보안 경고

보안 경고는 더 안전한 라이브러리 및 애플리케이션을 지원합니다. 이들 경고는 프로그램의 보안 결함을 방지하는 데 도움이 됩니다. 이들 경고를 비활성화하는 경우 코드에 그 이유를 명확하게 표시하고 개발 프로젝트의 지정된 보안 담당자에게 이 사실을 알려야 합니다.

## <a name="in-this-section"></a>섹션 내용

|규칙|설명|
|----------|-----------------|
|[CA2100: 보안상 취약한 부분이 있는지 SQL 쿼리를 검토하십시오.](../code-quality/ca2100.md)|메서드가 메서드에 대한 문자열 인수로부터 만들어진 문자열을 사용하여 System.Data.IDbCommand.CommandText 속성을 설정합니다. 이 규칙에서는 문자열 인수에 사용자 입력이 포함된 것으로 가정합니다. 사용자 입력으로부터 만들어진 SQL 명령 문자열은 SQL 삽입 공격에 취약합니다.|
|[CA2109: 표시되는 이벤트 처리기를 검토하세요.](../code-quality/ca2109.md)|public 또는 protected 이벤트 처리 메서드를 발견했습니다. 이벤트 처리 메서드는 반드시 필요한 경우를 제외하고 노출하면 안 됩니다.|
|[CA2119: private 인터페이스를 만족하는 메서드를 봉인하세요.](../code-quality/ca2119.md)|상속할 수 있는 public 형식에서는 internal(Visual Basic의 경우 Friend) 인터페이스의 재정의 가능한 메서드 구현을 제공합니다. 이 규칙 위반 문제를 해결하려면 어셈블리 외부에서 메서드가 재정의되지 않도록 합니다.|
|[CA2153: 손상된 상태 예외를 처리하지 마세요.](../code-quality/ca2153.md)|[CSE(손상된 상태 예외)](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions) 는 프로세스에 메모리 손상이 있음을 나타냅니다. 프로세스 충돌을 허용하는 대신 catch하면 공격자가 손상된 메모리 영역에 익스플로잇을 배치할 수 있는 경우 보안 취약점이 발생할 수 있습니다.|
|[CA2300: 안전하지 않은 역직렬 변환기 BinaryFormatter를 사용하지 마세요.](../code-quality/ca2300.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2301: 먼저 BinaryFormatter.Binder를 설정하지 않고 BinaryFormatter.Deserialize를 호출하지 마세요.](../code-quality/ca2301.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2302: BinaryFormatter.Deserialize를 호출하기 전에 BinaryFormatter.Binder가 설정되었는지 확인합니다.](../code-quality/ca2302.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2305: 안전하지 않은 역직렬 변환기 LosFormatter를 사용하지 마세요.](../code-quality/ca2305.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2310: 안전하지 않은 역직렬 변환기 NetDataContractSerializer를 사용하지 마세요.](../code-quality/ca2310.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2311: 먼저 NetDataContractSerializer.Binder를 설정하지 않고 역직렬화하지 마세요.](../code-quality/ca2311.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2312: 역직렬화하기 전에 NetDataContractSerializer.Binder를 설정해야 합니다.](../code-quality/ca2312.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2315: 안전하지 않은 역직렬 변환기 ObjectStateFormatter를 사용하지 마세요.](../code-quality/ca2315.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2321: SimpleTypeResolver를 사용하여 JavaScriptSerializer를 통해 역직렬화하지 마세요.](../code-quality/ca2321.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2322: JavaScriptSerializer가 역직렬화하기 전에 SimpleTypeResolver로 초기화되지 않는지 확인하세요.](../code-quality/ca2322.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2326: None 이외의 TypeNameHandling 값을 사용하지 마세요.](../code-quality/ca2326.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2327: 안전하지 않은 JsonSerializerSettings를 사용하지 마세요.](../code-quality/ca2327.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2328: JsonSerializerSettings가 안전한지 확인하세요.](../code-quality/ca2328.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2329: 안전하지 않은 구성을 사용하여 JsonSerializer로 역직렬화하지 마세요.](../code-quality/ca2329.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2330: 역직렬화할 때 JsonSerializer에 보안 구성이 있는지 확인하세요.](../code-quality/ca2330.md)|안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다.|
|[CA2350: DataTable.ReadXml()의 입력을 신뢰할 수 있는지 확인하세요.](ca2350.md)|신뢰할 수 없는 입력으로를 deserialize 할 때 <xref:System.Data.DataTable> 공격자는 서비스 거부 공격을 수행할 악성 입력을 만들 수 있습니다. 알 수 없는 원격 코드 실행 취약점이 있을 수 있습니다.|
|[CA2351: DataSet.ReadXml()의 입력을 신뢰할 수 있는지 확인하세요.](ca2351.md)|신뢰할 수 없는 입력으로를 deserialize 할 때 <xref:System.Data.DataSet> 공격자는 서비스 거부 공격을 수행할 악성 입력을 만들 수 있습니다. 알 수 없는 원격 코드 실행 취약점이 있을 수 있습니다.|
|[CA2352: 직렬화 가능 형식의 안전하지 않은 데이터 세트 또는 DataTable은 원격 코드 실행 공격에 취약할 수 있습니다.](ca2352.md)|로 표시 된 클래스 또는 구조체에 <xref:System.SerializableAttribute> <xref:System.Data.DataSet> 또는 <xref:System.Data.DataTable> 필드 또는 속성이 포함 되어 있고가 없는 <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> 경우|
|[CA2353: 직렬화 가능 형식의 안전하지 않은 데이터 세트 또는 DataTable입니다.](ca2353.md)|XML serialization 특성 또는 데이터 계약 특성으로 표시 된 클래스 또는 구조체에 <xref:System.Data.DataSet> 또는 <xref:System.Data.DataTable> 필드 또는 속성이 포함 되어 있습니다.|
|[CA2354: 역직렬화된 개체 그래프의 안전하지 않은 데이터 세트 또는 DataTable은 원격 코드 실행 공격에 취약할 수 있습니다.](ca2354.md)|Serialize 된로 deserialize <xref:System.Runtime.Serialization.IFormatter?displayProperty=nameWithType> 하 고, 캐스트 된 형식의 개체 그래프에 또는가 포함 될 수 있습니다 <xref:System.Data.DataSet> <xref:System.Data.DataTable> .|
|[CA2355: 역직렬화된 개체 그래프의 안전하지 않은 데이터 세트 또는 DataTable](ca2355.md)|캐스팅 되거나 지정 된 형식의 개체 그래프에 또는가 포함 될 수 있는 경우 deserialize <xref:System.Data.DataSet> <xref:System.Data.DataTable>|
|[CA2356: 웹 deserialize 된 개체 그래프의 안전 하지 않은 데이터 집합 또는 DataTable](ca2356.md)|또는를 사용 하는 메서드에 <xref:System.Web.Services.WebMethodAttribute?displayProperty=nameWithType> <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> 또는를 참조할 수 있는 매개 변수가 있습니다 <xref:System.Data.DataSet> <xref:System.Data.DataTable> .|
|[CA2361: DataSet.ReadXml()을 포함하는 자동 생성된 클래스가 신뢰할 수 없는 데이터와 함께 사용되지 않도록 하기](ca2361.md)|신뢰할 수 없는 입력으로를 deserialize 할 때 <xref:System.Data.DataSet> 공격자는 서비스 거부 공격을 수행할 악성 입력을 만들 수 있습니다. 알 수 없는 원격 코드 실행 취약점이 있을 수 있습니다.|
|[CA2362: 자동 생성된 직렬화 가능 형식의 안전하지 않은 DataSet 또는 DataTable은 원격 코드 실행 공격에 취약할 수 있음](ca2362.md)|를 사용 하 여 신뢰할 수 없는 입력 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 을 deserialize 하 고 deserialize 된 개체 그래프에 또는가 포함 된 경우 <xref:System.Data.DataSet> <xref:System.Data.DataTable> 공격자는 악의적인 페이로드를 만들어 원격 코드 실행 공격을 수행할 수 있습니다.|
|[CA3001: 코드에서 SQL 주입 취약점에 대해 검토합니다.](../code-quality/ca3001.md)|신뢰할 수 없는 입력 및 SQL 명령으로 작업 하는 경우 SQL 삽입 공격에 유의 해야 합니다. SQL 삽입 공격은 악의적인 SQL 명령을 실행 하 여 응용 프로그램의 보안 및 무결성을 손상 시킬 수 있습니다.|
|[CA3002: 코드에서 XSS 취약점에 대해 검토합니다.](../code-quality/ca3002.md)|웹 요청에서 신뢰할 수 없는 입력으로 작업할 때는 XSS (사이트 간 스크립팅) 공격에 주의 해야 합니다. XSS 공격은 신뢰할 수 없는 입력을 원시 HTML 출력에 삽입 하 여 공격자가 악의적인 스크립트를 실행 하거나 웹 페이지의 콘텐츠를 악의적으로 수정할 수 있도록 합니다.|
|[CA3003: 코드에서 파일 경로 삽입 취약성에 대해 검토합니다.](../code-quality/ca3003.md)|웹 요청에서 신뢰할 수 없는 입력으로 작업 하는 경우 파일에 대 한 경로를 지정 하는 경우 사용자가 제어 하는 입력을 사용할 수 있습니다.|
|[CA3004: 코드에서 정보 공개 취약성에 대해 검토합니다.](../code-quality/ca3004.md)|예외 정보를 공개 하면 공격자가 응용 프로그램의 내부 정보를 파악할 수 있으므로 공격자가 다른 취약점을 악용할 수 있습니다.|
|[CA3006: 코드에서 프로세스 명령 주입 취약점에 대해 검토합니다.](../code-quality/ca3006.md)|신뢰할 수 없는 입력으로 작업 하는 경우 명령 삽입 공격에 유의 해야 합니다. 명령 삽입 공격은 서버와의 보안 및 무결성을 손상 시키는 기본 운영 체제에서 악성 명령을 실행할 수 있습니다.|
|[CA3007: 코드에서 오픈 리디렉션 취약점에 대해 검토합니다.](../code-quality/ca3007.md)|신뢰할 수 없는 입력으로 작업 하는 경우 개방형 리디렉션 취약성에 유의 해야 합니다. 공격자는 오픈 리디렉션 취약성을 악용 하 여 합법적인 URL의 모양을 제공 하는 데 웹 사이트를 사용할 수 있지만, 의심 되는 방문자를 피싱 또는 기타 악성 웹 페이지로 리디렉션할 수 있습니다.|
|[CA3008: 코드에서 XPath 삽입 취약성에 대해 검토합니다.](../code-quality/ca3008.md)|신뢰할 수 없는 입력으로 작업할 때는 XPath 삽입 공격에 유의 해야 합니다. 신뢰할 수 없는 입력을 사용 하 여 XPath 쿼리를 생성 하면 공격자가 쿼리를 악의적으로 조작 하 여 의도 하지 않은 결과를 반환 하 고 쿼리 된 XML의 콘텐츠를 공개할 수 있습니다.|
|[CA3009: 코드에서 XML 삽입 취약성에 대해 검토합니다.](../code-quality/ca3009.md)|신뢰할 수 없는 입력으로 작업 하는 경우 XML 삽입 공격에 유의 해야 합니다.|
|[CA3010: 코드에서 XAML 삽입 취약성에 대해 검토합니다.](../code-quality/ca3010.md)|신뢰할 수 없는 입력으로 작업 하는 경우 XAML 삽입 공격에 유의 해야 합니다. XAML은 개체 인스턴스화 및 실행을 직접적으로 나타내는 태그 언어입니다. 즉, XAML로 생성 된 요소는 시스템 리소스 (예: 네트워크 액세스 및 파일 시스템 IO)와 상호 작용할 수 있습니다.|
|[CA3011: 코드에서 DLL 삽입 취약성에 대해 검토합니다.](../code-quality/ca3011.md)|신뢰할 수 없는 입력으로 작업할 때는 신뢰할 수 없는 코드를 로드 하는 것에 유의 해야 합니다. 웹 응용 프로그램이 신뢰할 수 없는 코드를 로드 하는 경우 공격자가 프로세스에 악성 Dll을 삽입 하 고 악성 코드를 실행할 수 있습니다.|
|[CA3012: 코드에서 regex 삽입 취약성에 대해 검토합니다.](../code-quality/ca3012.md)|신뢰할 수 없는 입력으로 작업할 때는 regex 삽입 공격에 유의 해야 합니다. 공격자는 regex 주입을 사용 하 여 정규식을 악의적으로 수정 하거나 regex가 의도 하지 않은 결과와 일치 하도록 하거나 regex가 과도 한 CPU를 사용 하 여 서비스 거부 공격을 내릴 수 있습니다.|
|[CA3061: URL로 스키마를 추가하지 마세요.](../code-quality/ca3061.md)|위험한 외부 참조를 유발할 수 있으므로 Add 메서드의 unsafe 오버 로드를 사용 하지 마세요.|
|[CA3075: DTD 처리가 안전하지 않습니다.](../code-quality/ca3075.md)|안전하지 않은 DTDProcessing 인스턴스를 사용하거나 외부 엔터티 소스를 참조하면 파서는 신뢰할 수 없는 입력을 허용하고 공격자에게 중요 한 정보를 공개할 수 있습니다.|
|[CA3076: XSLT 스크립트 실행이 안전하지 않습니다.](../code-quality/ca3076.md)|.NET 응용 프로그램에서 비보안 방식에서 XSLT (Extensible Stylesheet Language) 변환 (XSLT)을 실행 하는 경우 프로세서는 공격자에 게 중요 한 정보를 노출 하 여 서비스 거부 및 사이트 간 공격을 유발할 수 있는 신뢰할 수 없는 URI 참조를 해결할 수 있습니다.|
|[CA3077: API 디자인, XML 문서 및 XML 텍스트 판독기의 처리가 안전하지 않습니다.](../code-quality/ca3077.md)|XMLDocument 및 XMLTextReader에서 파생된 API를 디자인할 경우 DtdProcessing에 주의해야 합니다. 외부 엔터티 소스를 참조하거나 확인할 때 안전하지 않은 DTDProcessing 인스턴스를 사용하거나 XML에서 안전하지 않은 값을 설정하면 정보가 공개될 수 있습니다.|
|[CA3147: ValidateAntiForgeryToken을 사용하여 동사 처리기를 표시하세요.](../code-quality/ca3147.md)|ASP.NET MVC 컨트롤러를 설계할 때 사이트 간 요청 위조 공격을 염두에 둘 수 있습니다. 교차 사이트 요청 위조 공격은 인증 된 사용자의 악성 요청을 ASP.NET MVC 컨트롤러로 보낼 수 있습니다.|
|[CA5350: 취약한 암호화 알고리즘을 사용하지 마세요.](../code-quality/ca5350.md)|오늘날 여러 가지 이유로 약한 암호화 알고리즘 및 해시 함수가 사용되지만 데이터의 무결성과 기밀성을 보장하기 위해서는 이 방법을 사용하지 않아야 합니다. 이 규칙은 코드에 TripleDES, SHA1 또는 RIPEMD160 알고리즘이 있을 때 발생합니다.|
|[CA5351: 손상 된 암호화 알고리즘을 사용 하지 마십시오.](../code-quality/ca5351.md)|끊어진 암호화 알고리즘은 안전하지 않은 것으로 간주되므로 사용해서는 안 됩니다. 이 규칙은 코드에 MD5 해시 알고리즘 또는 DES나 RC2 암호화 알고리즘이 있을 때 트리거됩니다.|
|[CA5358: 안전하지 않은 암호화 모드를 사용하지 마세요.](../code-quality/ca5358.md)|안전하지 않은 암호화 모드를 사용하지 마세요.|
|[CA5359: 인증서 유효성 검사를 비활성화하지 마세요.](../code-quality/ca5359.md)|인증서는 서버의 id를 인증 하는 데 도움이 될 수 있습니다. 클라이언트는 서버 인증서의 유효성을 검사 하 여 요청이 원하는 서버로 전송 되도록 해야 합니다. ServerCertificateValidationCallback에서 항상를 반환 `true` 하는 경우 모든 인증서가 유효성 검사를 통과 합니다.|
|[CA5360: deserialization에서 위험한 메서드를 호출하지 마세요.](../code-quality/ca5360.md)|안전 하지 않은 deserialization은 신뢰할 수 없는 데이터를 사용 하 여 응용 프로그램의 논리를 남용 하거나, DoS (서비스 거부) 공격을 수행 하거나, deserialize 될 때 임의의 코드를 실행할 때 발생 하는 취약성입니다. 응용 프로그램에서 제어 하는 신뢰할 수 없는 데이터를 deserialize 하는 경우 악의적인 사용자가 이러한 deserialization 기능을 악용할 수 있습니다. 특히 deserialization 프로세스에서 위험한 메서드를 호출 합니다. 안전 하지 않은 deserialization 공격에 성공 하면 공격자가 DoS 공격, 인증 바이패스 및 원격 코드 실행과 같은 공격을 수행할 수 있습니다.|
|[CA5361: 강력한 암호의 SChannel 사용을 비활성화하지 마세요.](../code-quality/ca5361.md)|`Switch.System.Net.DontEnableSchUseStrongCrypto`를로 설정 `true` 하면 weakens TLS (전송 계층 보안) 연결에 사용 되는 암호화가 사용 됩니다. 약한 암호화는 응용 프로그램과 서버 간 통신의 기밀성을 손상 시켜 공격자가 중요 한 데이터를 보다 쉽게 도청 수 있도록 합니다.|
|[CA5362: 역직렬화된 개체 그래프의 잠재적 참조 주기](../code-quality/ca5362.md)|신뢰할 수 없는 데이터를 deserialize 하는 경우 deserialize 된 개체 그래프를 처리 하는 모든 코드는 무한 루프로 이동 하지 않고 참조 주기를 처리 해야 합니다. 여기에는 deserialization 콜백의 일부인 코드와 deserialization 완료 후 개체 그래프를 처리 하는 코드가 모두 포함 됩니다. 그렇지 않으면 공격자가 참조 주기를 포함 하는 악성 데이터를 사용 하 여 서비스 거부 공격을 수행할 수 있습니다.|
|[CA5363: 요청 유효성 검사를 사용하지 않도록 설정하지 마세요.](../code-quality/ca5363.md)|요청 유효성 검사는 HTTP 요청을 검사 하 고 사이트 간 스크립팅을 포함 하 여 삽입 공격으로 이어질 수 있는 잠재적으로 위험한 콘텐츠가 포함 되어 있는지 여부를 확인 하는 ASP.NET의 기능입니다.|
|[CA5364: 사용되지 않는 보안 프로토콜을 사용하지 마세요.](../code-quality/ca5364.md)|TLS (전송 계층 보안)는 일반적으로 http (하이퍼텍스트 전송 프로토콜 보안)를 사용 하는 컴퓨터 간의 통신을 보호 합니다. 이전 프로토콜 버전의 TLS는 TLS 1.2 및 TLS 1.3 보다 안전 하지 않으며 새로운 취약성이 있을 가능성이 높습니다. 위험을 최소화 하기 위해 이전 프로토콜 버전을 사용 하지 않습니다.|
|[CA5365: HTTP 헤더 검사를 사용하지 않도록 설정하지 마세요.](../code-quality/ca5365.md)|HTTP 헤더 검사는 응답 헤더에 있는 캐리지 리턴 및 줄 바꿈 문자 (\r 및 \n)의 인코딩을 사용할 수 있도록 합니다. 이 인코딩 헤더에 포함 된 신뢰할 수 없는 데이터를 표시 하는 애플리케이션을 악용 하는 삽입 공격을 방지 하는 데 도움이 됩니다.|
|[CA5366: 데이터 세트 읽기 XML에 XmlReader를 사용하세요.](../code-quality/ca5366.md)|를 사용 하 여 <xref:System.Data.DataSet> 신뢰할 수 없는 데이터가 있는 XML을 읽으면 <xref:System.Xml.XmlReader> 보안 해결 프로그램을 사용 하거나 DTD 처리를 사용할 수 없는를 사용 하 여 제한 해야 하는 위험한 외부 참조가 로드 될 수 있습니다.|
|[CA5367: 포인터 필드를 사용하여 형식을 직렬화하지 마세요.](../code-quality/ca5367.md)|이 규칙은 포인터 필드 또는 속성이 있는 serializable 클래스가 있는지 여부를 확인 합니다. Serialize 할 수 없는 멤버는 정적 멤버 또는로 표시 된 필드와 같은 포인터 일 수 있습니다 <xref:System.NonSerializedAttribute> .|
|[CA5368: Page에서 파생된 클래스의 ViewStateUserKey를 설정하세요.](../code-quality/ca5368.md)|속성을 설정 하면 공격자가 변수를 사용 하 여 <xref:System.Web.UI.Page.ViewStateUserKey> 공격을 생성할 수 없도록 개별 사용자의 뷰 상태 변수에 식별자를 할당할 수 있으므로 응용 프로그램에 대 한 공격을 방지할 수 있습니다. 그렇지 않으면 교차 사이트 요청 위조에 대 한 취약성이 있습니다.|
|[CA5369: 역직렬화에 XmlReader를 사용하세요.](../code-quality/ca5369.md)|신뢰할 수 없는 DTD 및 XML 스키마를 처리 하면 보안 해결 프로그램이 포함 된 XmlReader를 사용 하 여 제한 하거나 DTD 및 XML 인라인 스키마 처리를 사용 하지 않도록 설정 해야 하는 위험한 외부 참조를 로드할 수 있습니다.|
|[CA5370: 판독기 유효성 검사에 XmlReader를 사용하세요.](../code-quality/ca5370.md)|신뢰할 수 없는 DTD 및 XML 스키마를 처리 하면 위험한 외부 참조를 로드할 수 있습니다. 이 위험한 로드는 보안 해결 프로그램이 포함 된 XmlReader를 사용 하거나 DTD 및 XML 인라인 스키마 처리를 사용 하지 않도록 설정 하 여 제한할 수 있습니다.|
|[CA5371: 스키마 읽기에 XmlReader를 사용하세요.](../code-quality/ca5371.md)|신뢰할 수 없는 DTD 및 XML 스키마를 처리 하면 위험한 외부 참조를 로드할 수 있습니다. 보안 해결 프로그램을 사용 하거나 DTD 및 XML 인라인 스키마 처리를 사용 하지 않는 XmlReader를 사용 하면이이 제한 됩니다.|
|[CA5372: XPathDocument에 XmlReader를 사용하세요.](../code-quality/ca5372.md)|신뢰할 수 없는 데이터에서 XML을 처리 하면 위험한 외부 참조가 로드 될 수 있으며,이는 보안 해결 프로그램이 포함 된 XmlReader를 사용 하 여 제한 하거나 DTD 처리를 사용 하지 않도록 설정할 수 있습니다.|
|[CA5373: 사용되지 않는 키 파생 함수를 사용하지 마세요.](../code-quality/ca5373.md)|이 규칙은 약한 키 파생 메서드 및의 호출을 검색 합니다 <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> `Rfc2898DeriveBytes.CryptDeriveKey` . <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> 약한 알고리즘 PBKDF1을 사용 했습니다.|
|[CA5374: XslTransform을 사용하지 마세요.](../code-quality/ca5374.md)|이 규칙 <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> 은가 코드에서 인스턴스화되어 있는지 확인 합니다. <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> 는 이제 사용 되지 않으며 사용할 수 없습니다.|
|[CA5375: 계정 공유 액세스 시그니처를 사용하지 마세요.](../code-quality/ca5375.md)|계정 SAS는 서비스 SAS로 허용 되지 않는 blob 컨테이너, 테이블, 큐 및 파일 공유에 대 한 읽기, 쓰기 및 삭제 작업에 대 한 액세스를 위임할 수 있습니다. 그러나 컨테이너 수준 정책을 지원 하지 않으며 부여 된 사용 권한에 대 한 유연성과 제어 수준이 낮습니다. 악의적인 사용자가이를 가져오면 저장소 계정이 쉽게 손상 됩니다.|
|[CA5376: SharedAccessProtocol HttpsOnly를 사용하세요.](../code-quality/ca5376.md)|SAS는 HTTP에서 일반 텍스트로 전송할 수 없는 중요 한 데이터입니다.|
|[CA5377: 컨테이너 수준 액세스 정책을 사용하세요.](../code-quality/ca5377.md)|컨테이너 수준 액세스 정책은 언제 든 지 수정 하거나 취소할 수 있습니다. 이를 통해 부여 되는 사용 권한을 보다 유연 하 게 제어할 수 있습니다.|
|[CA5378: ServicePointManagerSecurityProtocols를 비활성화하지 마세요.](../code-quality/ca5378.md)|`Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols`로 설정 `true` 하면 Windows Communication FRAMEWORK의 Tls (전송 계층 보안) 연결을 tls 1.0을 사용 하도록 제한 합니다. 해당 버전의 TLS는 더 이상 사용 되지 않습니다.|
|[CA5379: 취약한 키 파생 함수 알고리즘은 사용하지 마세요.](../code-quality/ca5379.md)|<xref:System.Security.Cryptography.Rfc2898DeriveBytes>클래스는 기본적으로 알고리즘을 사용 <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> 합니다. 이상에서 생성자의 일부 오버 로드에 사용할 해시 알고리즘을 지정 해야 합니다 <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> . 속성에는 <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> 접근자만 있으며 `get` 한정자가 없습니다 `overriden` .|
|[CA5380: 루트 저장소에 인증서를 추가하지 마세요.](../code-quality/ca5380.md)|이 규칙은 신뢰할 수 있는 루트 인증 기관 인증서 저장소에 인증서를 추가 하는 코드를 검색 합니다. 기본적으로 신뢰할 수 있는 루트 인증 기관 인증서 저장소는 Microsoft 루트 인증서 프로그램의 요구 사항을 충족 하는 공용 Ca 집합을 사용 하 여 구성 됩니다.|
|[CA5381: 인증서가 루트 저장소에 추가되지 않았는지 확인하세요.](../code-quality/ca5381.md)|이 규칙은 잠재적으로 신뢰할 수 있는 루트 인증 기관 인증서 저장소에 인증서를 추가 하는 코드를 검색 합니다. 기본적으로 신뢰할 수 있는 루트 인증 기관 인증서 저장소는 Microsoft 루트 인증서 프로그램의 요구 사항을 충족 하는 공용 Ca (인증 기관) 집합으로 구성 됩니다.|
|[CA5382: ASP.NET Core에서 보안 쿠키를 사용하세요.](../code-quality/ca5382.md)|HTTPS를 통해 사용할 수 있는 응용 프로그램은 보안 쿠키를 사용 해야 합니다 .이 쿠키는 TLS (전송 계층 보안)를 사용 하 여 쿠키를 전송 해야 함을 브라우저에 표시 합니다.|
|[CA5383: ASP.NET Core에서 보안 쿠키를 사용해야 합니다.](../code-quality/ca5383.md)|HTTPS를 통해 사용할 수 있는 응용 프로그램은 보안 쿠키를 사용 해야 합니다 .이 쿠키는 TLS (전송 계층 보안)를 사용 하 여 쿠키를 전송 해야 함을 브라우저에 표시 합니다.|
|[CA5384: DSA(디지털 시그니처 알고리즘)를 사용하지 마세요.](../code-quality/ca5384.md)|DSA는 약한 비대칭 암호화 알고리즘입니다.|
|[CA5385: 충분한 키 크기로 RSA(Rivest–Shamir–Adleman) 알고리즘을 사용하세요.](../code-quality/ca5385.md)|2048 비트 보다 작은 RSA 키는 무차별 암호 대입 공격에 보다 취약 합니다.|
|[CA5386: SecurityProtocolType 값을 하드 코딩하지 마세요.](../code-quality/ca5386.md)|TLS (전송 계층 보안)는 일반적으로 http (하이퍼텍스트 전송 프로토콜 보안)를 사용 하는 컴퓨터 간의 통신을 보호 합니다. 프로토콜 버전 TLS 1.0 및 TLS 1.1은 사용 되지 않지만 TLS 1.2 및 TLS 1.3은 최신 상태입니다. 향후에는 TLS 1.2 및 TLS 1.3이 더 이상 사용 되지 않을 수 있습니다. 응용 프로그램의 보안을 유지 하려면 프로토콜 버전을 하드 코딩 하지 않고 .NET Framework v 4.7.1 이상을 대상으로 해야 합니다.|
|[CA5387: 부족한 반복 횟수로 취약한 키 파생 함수를 사용하지 마세요.](../code-quality/ca5387.md)|이 규칙은 암호화 키가 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> 10만 보다 작은 반복 횟수를 사용 하 여 생성 되었는지 확인 합니다. 반복 횟수를 높이면 생성 된 암호화 키를 추측 하려고 시도 하는 사전 공격을 줄일 수 있습니다.|
|[CA5388: 취약한 키 파생 함수를 사용할 때 충분한 반복 횟수가 필요합니다.](../code-quality/ca5388.md)|이 규칙은 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> 10만 보다 작은 반복 횟수를 사용 하 여 암호화 키가 생성 되었는지 확인 합니다. 반복 횟수를 높이면 생성 된 암호화 키를 추측 하려고 시도 하는 사전 공격을 줄일 수 있습니다.|
|[CA5389: 대상 파일 시스템 경로에 보관 항목의 경로를 추가하지 마세요.](../code-quality/ca5389.md)|파일 경로는 상대적일 수 있으며, 예상 된 파일 시스템 대상 경로 외부에서 파일 시스템에 액세스할 수 있으며,이로 인해 악의적인 구성 변경 내용 및 대기 방식 기술을 통해 원격 코드를 실행할 수 있습니다.|
|[CA5390: 암호화 키를 하드 코딩하지 마세요.](../code-quality/ca5390.md)|대칭 알고리즘을 성공적으로 수행 하려면 비밀 키를 발신자와 수신자 에게만 인식 해야 합니다. 키가 하드 코드 되 면 쉽게 검색 됩니다. 컴파일된 이진 파일의 경우에도 악의적인 사용자가 쉽게 추출할 수 있습니다. 개인 키가 손상 되 면 암호화 텍스트를 직접 해독 하 여 더 이상 보호할 수 없습니다.|
|[CA5391: ASP.NET Core MVC 컨트롤러에서 위조 방지 토큰을 사용하세요.](../code-quality/ca5391.md)|`POST` `PUT` `PATCH` `DELETE` 위조 방지 토큰의 유효성을 검사 하지 않고,, 또는 요청을 처리 하면 교차 사이트 요청 위조 공격에 취약할 수 있습니다. 사이트 간 요청 위조 공격은 인증 된 사용자의 악성 요청을 ASP.NET Core MVC 컨트롤러로 보낼 수 있습니다.|
|[CA5392: P/Invokes에 DefaultDllImportSearchPaths 특성을 사용하세요.](../code-quality/ca5392.md)|기본적으로 P/Invoke 함수는 <xref:System.Runtime.InteropServices.DllImportAttribute> 로드 하는 라이브러리에 대 한 현재 작업 디렉터리를 포함 하 여 많은 디렉터리를 검색 합니다. 이는 특정 응용 프로그램에 대 한 보안 문제 이며 DLL 하이재킹이 될 수 있습니다.|
|[CA5393: 안전하지 않은 DllImportSearchPath 값을 사용하지 마세요.](../code-quality/ca5393.md)|기본 DLL 검색 디렉터리와 어셈블리 디렉터리에 악성 DLL이 있을 수 있습니다. 또는 응용 프로그램이 실행 되는 위치에 따라 응용 프로그램 디렉터리에 악성 DLL이 있을 수 있습니다.|
|[CA5394: 안전하지 않은 임의성을 사용하지 마세요.](../code-quality/ca5394.md)|공격자는 암호화 된 약한 의사 난수 생성기를 사용 하 여 보안에 중요 한 값이 생성 되는 것을 예측할 수 있습니다.|
|[CA5395: 작업 메서드의 HttpVerb 특성이 없습니다.](../code-quality/ca5395.md)|데이터를 만들거나 편집, 삭제 또는 수정 하는 모든 작업 메서드는 사이트 간 요청 위조 공격 으로부터 위조 방지 특성으로 보호 해야 합니다. GET 작업을 수행 하는 것은 부작용이 없으며 지속형 데이터를 수정 하지 않는 안전 작업 이어야 합니다.|
|[CA5396: HttpCookie에 대해 HttpOnly를 true로 설정하세요.](../code-quality/ca5396.md)|심층 방어 수단으로 보안에 민감한 HTTP 쿠키가 HttpOnly로 표시 되어 있는지 확인 합니다. 이는 웹 브라우저에서 스크립트가 쿠키에 액세스 하지 못하도록 하는 것을 의미 합니다. 삽입 된 악성 스크립트는 쿠키를 도용 하는 일반적인 방법입니다.|
|[CA5397: 사용되지 않는 SslProtocols 값을 사용하지 마세요.](../code-quality/ca5397.md)|TLS (전송 계층 보안)는 일반적으로 http (하이퍼텍스트 전송 프로토콜 보안)를 사용 하는 컴퓨터 간의 통신을 보호 합니다. 이전 프로토콜 버전의 TLS는 TLS 1.2 및 TLS 1.3 보다 안전 하지 않으며 새로운 취약성이 있을 가능성이 높습니다. 위험을 최소화 하기 위해 이전 프로토콜 버전을 사용 하지 않습니다.|
|[CA5398: SslProtocols 값을 하드 코딩하지 마세요.](../code-quality/ca5398.md)|TLS (전송 계층 보안)는 일반적으로 http (하이퍼텍스트 전송 프로토콜 보안)를 사용 하는 컴퓨터 간의 통신을 보호 합니다. 프로토콜 버전 TLS 1.0 및 TLS 1.1은 사용 되지 않지만 TLS 1.2 및 TLS 1.3은 최신 상태입니다. 향후에는 TLS 1.2 및 TLS 1.3이 더 이상 사용 되지 않을 수 있습니다. 응용 프로그램이 안전 하 게 유지 되도록 하려면 프로토콜 버전을 하드 코딩 하지 마십시오.|
|[CA5399: HttpClient 인증서 해지 목록 확인을 사용하지 않도록 명시적으로 설정하세요.](../code-quality/ca5399.md)|해지 된 인증서를 더 이상 신뢰할 수 없습니다. 공격자는 악성 데이터를 전달 하거나 HTTPS 통신에서 중요 한 데이터를 도용 하는 데 사용할 수 있습니다.|
|[CA5400: HttpClient 인증서 해지 목록 확인을 사용할 수 있는지 확인합니다.](../code-quality/ca5400.md)|해지 된 인증서를 더 이상 신뢰할 수 없습니다. 공격자는 악성 데이터를 전달 하거나 HTTPS 통신에서 중요 한 데이터를 도용 하는 데 사용할 수 있습니다.|
|[CA5401: 기본이 아닌 IV와 함께 CreateEncryptor를 사용하지 마세요.](../code-quality/ca5401.md)|대칭 암호화는 항상 반복 되지 않는 초기화 벡터를 사용 하 여 사전 공격을 방지 해야 합니다.|
|[CA5402: 기본 IV와 함께 CreateEncryptor를 사용하세요.](../code-quality/ca5402.md)|대칭 암호화는 항상 반복 되지 않는 초기화 벡터를 사용 하 여 사전 공격을 방지 해야 합니다.|
|[CA5403: 인증서 하드 코딩 안 함](../code-quality/ca5403.md)|`data` `rawData` 또는 생성자의 또는 매개 변수는 <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 하드 코드 되어 있습니다.|
