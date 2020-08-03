---
ms.openlocfilehash: 557d811e2eeaf926cb958471d214fc23c50a25f2
ms.sourcegitcommit: 43df639b2cd99200f725a8ebb941477481a6f0ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87471581"
---
- 대신 보안 serializer를 사용 하 고 **공격자가 deserialize 할 임의의 형식을 지정할 수 없도록**합니다. 자세한 내용은 [기본 설정 대체](/dotnet/standard/serialization/binaryformatter-security-guide#preferred-alternatives)항목을 참조 하세요.
- Serialize 된 데이터를 변조 방지로 설정 합니다. Serialization 후 직렬화 된 데이터를 암호화 하 여 서명 합니다. Deserialization 전에 암호화 서명 유효성을 검사 합니다. 암호화 키가 공개 되지 않도록 보호 하 고 키 회전을 설계 합니다.
- 이 옵션을 사용 하면 코드를 서비스 거부 공격에 취약 하 고 향후 원격 코드 실행 공격이 발생할 수 있습니다. 자세한 내용은 [Binaryformatter 보안 가이드](/dotnet/standard/serialization/binaryformatter-security-guide)를 참조 하세요. Deserialize 된 형식을 제한 합니다. 사용자 지정를 구현 <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType> 합니다. Deserialize 하기 전에 `Binder` <xref:System.Runtime.Serialization.SerializationBinder> 모든 코드 경로에서 사용자 지정의 인스턴스로 속성을 설정 합니다. 재정의 된 <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> 메서드에서 형식이 예기치 않은 경우 예외를 throw 하 여 deserialization을 중지 합니다.
