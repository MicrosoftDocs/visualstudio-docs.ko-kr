---
title: 관리 코드에 대한 관리 권장 규칙 규칙 집합
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 875f6b3aba88fa3786e4c303f23072e586c4848d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75587344"
---
# <a name="managed-recommended-rules-rule-set-for-managed-code"></a>관리 코드에 대한 관리 권장 규칙 규칙 집합

Microsoft 관리 권장 규칙 규칙 집합을 사용 하 여 잠재적 보안 허점, 응용 프로그램 충돌 및 기타 중요 한 논리 및 디자인 오류를 비롯 하 여 관리 코드의 가장 중요 한 문제에 초점을 맞출 수 있습니다. 이 규칙 집합은 [관리 되는 최소 규칙](managed-minimum-rules-rule-set-for-managed-code.md) 규칙 집합의 모든 규칙을 포함 합니다.

프로젝트에 대해 만드는 모든 사용자 지정 규칙 집합에이 규칙 집합을 포함 합니다.

|규칙|설명|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|삭제 가능한 필드가 있는 형식은 삭제 가능해야 합니다.|
|[CA1009](../code-quality/ca1009.md)|이벤트 처리기를 제대로 선언하십시오.|
|[CA1016](../code-quality/ca1016.md)|AssemblyVersionAttribute로 어셈블리 표시|
|[CA1033](../code-quality/ca1033.md)|인터페이스 메서드는 자식 형식에서 호출할 수 있어야 합니다.|
|[CA1049](../code-quality/ca1049.md)|네이티브 리소스가 있는 형식은 삭제 가능해야 합니다.|
|[CA1060](../code-quality/ca1060.md)|P/Invoke를 NativeMethods 클래스로 이동|
|[CA1061](../code-quality/ca1061.md)|기본 클래스 메서드를 숨기지 마십시오.|
|[CA1063](../code-quality/ca1063.md)|IDisposable을 올바르게 구현하십시오.|
|[CA1065](../code-quality/ca1065.md)|예기치 않은 위치에서 예외를 발생시키지 마십시오.|
|[CA1301](../code-quality/ca1301.md)|중복 액셀러레이터 키를 사용하지 마십시오.|
|[CA1400](../code-quality/ca1400.md)|P/Invoke 진입점이 있어야 합니다.|
|[CA1401](../code-quality/ca1401.md)|P/Invoke는 노출되지 않아야 합니다.|
|[CA1403](../code-quality/ca1403.md)|자동 레이아웃 형식은 COM 노출이면 안 됩니다.|
|[CA1404](../code-quality/ca1404.md)|P/Invoke 다음에 바로 GetLastError를 호출하십시오.|
|[CA1405](../code-quality/ca1405.md)|COM 노출 형식의 기본 형식은 COM 노출이어야 합니다.|
|[CA1410](../code-quality/ca1410.md)|COM 등록 메서드는 일치해야 합니다.|
|[CA1415](../code-quality/ca1415.md)|P/Invoke를 올바르게 선언하십시오.|
|[CA1821](../code-quality/ca1821.md)|빈 종료자를 제거하십시오.|
|[CA1900](../code-quality/ca1900.md)|값 형식 필드는 이식 가능해야 합니다.|
|[CA1901](../code-quality/ca1901.md)|P/Invoke 선언은 이식 가능해야 합니다.|
|[CA2002](../code-quality/ca2002.md)|약한 ID를 가진 개체를 잠그지 마십시오.|
|[CA2100](../code-quality/ca2100.md)|보안상 취약한 부분이 있는지 SQL 쿼리를 검토하십시오.|
|[CA2101](../code-quality/ca2101.md)|P/Invoke 문자열 인수에 대해 마샬링을 지정하십시오.|
|[CA2108](../code-quality/ca2108.md)|값 형식에서 선언적 보안을 검토하십시오.|
|[CA2111](../code-quality/ca2111.md)|포인터는 노출되면 안 됩니다.|
|[CA2112](../code-quality/ca2112.md)|보안 형식은 필드를 노출하면 안 됩니다.|
|[CA2114](../code-quality/ca2114.md)|메서드 보안은 형식의 상위 집합이어야 합니다.|
|[CA2116](../code-quality/ca2116.md)|APTCA 메서드는 APTCA 메서드만 호출해야 합니다.|
|[CA2117](../code-quality/ca2117.md)|APTCA 형식은 APTCA 기본 형식만 확장해야 합니다.|
|[CA2122](../code-quality/ca2122.md)|링크 요청이 있는 메서드를 간접적으로 노출하지 마십시오.|
|[CA2123](../code-quality/ca2123.md)|재정의 링크 요청은 기본 링크 요청과 같아야 합니다.|
|[CA2124](../code-quality/ca2124.md)|취약한 finally 절을 외부 try에 래핑하십시오.|
|[CA2126](../code-quality/ca2126.md)|형식 링크 요청에는 상속 요청이 필요합니다.|
|[CA2131](../code-quality/ca2131.md)|보안에 중요한 형식은 형식 동등에 참여할 수 없습니다.|
|[CA2132](../code-quality/ca2132.md)|기본 생성자는 기본 형식의 기본 생성자 이상으로 중요해야 합니다.|
|[CA2133](../code-quality/ca2133.md)|대리자는 투명도가 일관된 메서드에 바인딩되어야 합니다.|
|[CA2134](../code-quality/ca2134.md)|메서드는 기본 메서드를 재정의할 때 일관된 투명도를 유지해야 합니다.|
|[CA2137](../code-quality/ca2137.md)|투명 메서드에는 확인할 수 있는 IL만 포함되어야 합니다.|
|[CA2138](../code-quality/ca2138.md)|투명 메서드는 SuppressUnmanagedCodeSecurity 특성을 사용하여 메서드를 호출해서는 안 됩니다.|
|[CA2140](../code-quality/ca2140.md)|투명 코드는 보안에 중요한 항목을 참조해서는 안 됩니다.|
|[CA2141](../code-quality/ca2141.md)|투명 메서드는 LinkDemands를 충족해서는 안 됩니다|
|[CA2146](../code-quality/ca2146.md)|형식은 기본 형식 및 인터페이스 이상으로 중요해야 합니다.|
|[CA2147](../code-quality/ca2147.md)|투명 메서드는 보안 어설션을 사용할 수 없습니다.|
|[CA2149](../code-quality/ca2149.md)|투명 메서드는 네이티브 코드를 호출해서는 안 됩니다.|
|[CA2200](../code-quality/ca2200.md)|스택 정보를 유지하도록 다시 throw하십시오.|
|[CA2202](../code-quality/ca2202.md)|개체를 여러 번 삭제하지 마십시오.|
|[CA2207](../code-quality/ca2207.md)|값 형식 정적 필드 인라인을 초기화하십시오.|
|[CA2212](../code-quality/ca2212.md)|서비스 구성 요소를 WebMethod를 사용하여 표시하지 마십시오.|
|[CA2213](../code-quality/ca2213.md)|삭제 가능한 필드는 삭제해야 합니다.|
|[CA2214](../code-quality/ca2214.md)|재정의 가능한 메서드를 생성자에서 호출하지 마십시오.|
|[CA2216](../code-quality/ca2216.md)|삭제 가능한 형식은 종료자를 선언해야 합니다.|
|[CA2220](../code-quality/ca2220.md)|종료자는 기본 클래스 종료자를 호출해야 합니다.|
|[CA2229](../code-quality/ca2229.md)|serialization 생성자를 구현하십시오.|
|[CA2231](../code-quality/ca2231.md)|ValueType.Equals를 재정의할 때 같음 연산자를 오버로드하십시오.|
|[CA2232](../code-quality/ca2232.md)|Windows Forms 진입점을 STAThread를 사용하여 표시하십시오.|
|[CA2235](../code-quality/ca2235.md)|모두 serialize할 수 없는 필드로 표시하십시오.|
|[CA2236](../code-quality/ca2236.md)|ISerializable 형식에서 기본 클래스 메서드를 호출하십시오.|
|[CA2237](../code-quality/ca2237.md)|SerializableAttribute로 ISerializable 형식 표시|
|[CA2238](../code-quality/ca2238.md)|serialization 메서드를 올바르게 구현하십시오.|
|[CA2240](../code-quality/ca2240.md)|ISerializable을 올바르게 구현하십시오.|
|[CA2241](../code-quality/ca2241.md)|서식 지정 메서드에 올바른 인수를 제공하십시오.|
|[CA2242](../code-quality/ca2242.md)|NaN에 대해 정확하게 테스트하십시오.|
