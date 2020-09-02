---
title: '인터페이스 추출 리팩터링 (c #) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fdcf281e1ace40d1d7cdac0be302810ea173581b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667559"
---
# <a name="extract-interface-refactoring-c"></a>인터페이스 추출 리팩터링(C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

인터페이스 추출은 기존 클래스, 구조체 또는 인터페이스에서 파생 된 멤버를 사용 하 여 새 인터페이스를 만드는 쉬운 방법을 제공 하는 리팩터링 작업입니다.

 여러 클라이언트가 클래스, 구조체 또는 인터페이스에서 멤버의 동일한 하위 집합을 사용 하거나 여러 클래스, 구조체 또는 인터페이스에 공통 된 멤버의 하위 집합이 있는 경우에는 인터페이스에서 멤버의 하위 집합을 구체화 하는 것이 유용할 수 있습니다. 인터페이스를 사용 하는 방법에 대 한 자세한 내용은 [인터페이스](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)를 참조 하세요.

 인터페이스 추출은 새 파일에 인터페이스를 생성 하 고 새 파일의 시작 부분에 커서를 놓습니다. **인터페이스 추출** 대화 상자를 사용 하 여 새 인터페이스로 추출할 멤버, 새 인터페이스의 이름 및 생성 된 파일의 이름을 지정할 수 있습니다.

### <a name="to-use-extract-interface"></a>Extract 인터페이스를 사용 하려면

1. 이라는 콘솔 응용 프로그램을 만들고 `ExtractInterface` 를 `Program` 다음 코드로 바꿉니다.

    ```csharp
    // Invoke Extract Interface on ProtoA.
    // Note:  the extracted interface will be created in a new file.
    class ProtoA
    {
        public void MethodB(string s) { }
    }
    ```

2. 에 커서가 배치 된 상태에서 `MethodB` **리팩터링** 메뉴에서 **인터페이스 추출** 을 클릭 합니다.

     **인터페이스 추출** 대화 상자가 나타납니다.

     바로 가기 키 CTRL + R을 입력 하 여 **인터페이스 추출** 대화 상자를 표시할 수도 있습니다.

     마우스 오른쪽 단추를 클릭 하 고 **리팩터링**을 가리킨 다음 **인터페이스 추출** 을 클릭 하 여 **인터페이스 추출** 대화 상자를 표시할 수도 있습니다.

3. **모두 선택**을 클릭 합니다.

4. **확인**을 클릭합니다.

     새 파일인 IProtoA.cs 및 다음 코드가 표시 됩니다.

    ```csharp
    using System;
    namespace TopThreeRefactorings
    {
        interface IProtoA
        {
            void MethodB(string s);
        }
    }
    ```

## <a name="remarks"></a>설명
 이 기능은 추출 하려는 멤버를 포함 하는 클래스, 구조체 또는 인터페이스에 커서가 있을 때에만 액세스할 수 있습니다. 커서가이 위치에 있으면 인터페이스 추출 리팩터링 작업을 호출 합니다.

 클래스 또는 구조체에서 extract 인터페이스를 호출 하는 경우 기본 및 인터페이스 목록이 새 인터페이스 이름을 포함 하도록 수정 됩니다. 인터페이스에서 extract 인터페이스를 호출 하면 기본 및 인터페이스 목록이 수정 되지 않습니다.

## <a name="see-also"></a>관련 항목
 [리팩터링(C#)](../csharp-ide/refactoring-csharp.md)