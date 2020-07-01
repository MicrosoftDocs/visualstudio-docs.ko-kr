---
author: dotpaul
ms.author: paulming
ms.date: 05/01/2019
ms.topic: include
ms.openlocfilehash: bc423f10cfbae0b7a0cdaedb72f6891a0e12d228
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68147108"
---
- 가능 하면 보안 serializer를 대신 사용 하 고 **공격자가 deserialize 할 임의의 형식을 지정할 수 없도록**합니다. 몇 가지 안전한 serializer는 다음과 같습니다.
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>-사용 하지 마세요 <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType> . 형식 확인자를 사용 해야 하는 경우 deserialize 된 형식을 예상 목록으로 제한 합니다.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft.json Json.NET-TypeNameHandling를 사용 합니다. TypeNameHandling에 다른 값을 사용 해야 하는 경우 사용자 지정 ISerializationBinder를 사용 하 여 deserialize 된 형식을 예상 목록으로 제한 합니다.
  - 프로토콜 버퍼
- Serialize 된 데이터를 변조 방지로 설정 합니다. Serialization 후 직렬화 된 데이터를 암호화 하 여 서명 합니다. Deserialization 전에 암호화 서명 유효성을 검사 합니다. 암호화 키가 공개 되지 않도록 보호 하 고 키 회전을 설계 합니다.