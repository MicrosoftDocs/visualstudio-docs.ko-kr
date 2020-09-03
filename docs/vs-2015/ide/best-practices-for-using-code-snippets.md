---
title: 코드 조각을 사용하는 방법에 대한 유용한 정보 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
ms.assetid: a293ec17-4dd7-4a99-8eeb-99f44a822a8b
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 74da305b69a9561573466d385c5d7b686da3693f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72620321"
---
# <a name="best-practices-for-using-code-snippets"></a>코드 조각을 사용하는 방법에 대한 유용한 정보
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코드 조각의 코드에는 작업을 수행하는 가장 기본적인 방법만 표시됩니다. 대부분 애플리케이션에서는 애플리케이션에 맞게 코드를 수정해야 합니다.

## <a name="handling-exceptions"></a>예외 처리
 일반적으로 코드 조각 Try…Catch 블록은 모든 예외를 catch 및 다시 throw합니다. 이는 프로젝트에 적합한 선택이 아닐 수 있습니다. 각 예외에 대한 여러 가지 응답 방법이 있습니다. 예를 들어 [방법: try/catch를 사용하여 예외 처리(C# 프로그래밍 가이드)](https://msdn.microsoft.com/library/ca8e3773-980e-4767-8633-7408540e9818) 및 [Try...Catch...Finally 문 ](https://msdn.microsoft.com/library/d6488026-ccb3-42b8-a810-0d97b9d6472b)을 참조하세요.

## <a name="file-locations"></a>파일 위치
 애플리케이션에 맞게 파일 위치를 조정할 경우 다음을 고려해야 합니다.

- 액세스 가능한 위치 찾기. 사용자에게 컴퓨터의 Program Files 폴더에 대한 액세스 권한이 없을 수 있으므로 애플리케이션 파일과 함께 파일이 저장되지 않을 수 있습니다.

- 안전한 위치 찾기. 파일을 루트 폴더(C:\\)에 저장하는 것은 안전하지 않습니다. 애플리케이션 데이터의 경우 \Application Data 폴더를 사용하는 것이 좋습니다. 개별 사용자 데이터의 경우 애플리케이션에서 \My Documents 폴더에 각 사용자에 대한 파일을 만들 수 있습니다.

- 유효한 파일 이름 사용. <xref:System.Windows.Forms.OpenFileDialog> 및 <xref:System.Windows.Forms.SaveFileDialog> 컨트롤을 사용하여 잘못된 파일 이름을 사용할 가능성을 줄일 수 있습니다. 사용자가 파일을 선택한 시간과 코드에서 파일을 조작한 시간 사이에 파일이 삭제되었을 수 있습니다. 또한 사용자에게 파일에 쓸 권한이 없을 수 있습니다.

## <a name="security"></a>보안
 조각의 보안 강도는 조각이 소스 코드에서 사용되는 위치 및 코드에 삽입된 후 수정되는 방법에 따라 달라집니다. 다음 목록에 있는 몇 가지 영역을 고려해야 합니다.

- 파일 및 데이터베이스 액세스

- 코드 액세스 보안

- 리소스 보호(예: 이벤트 로그, 레지스트리)

- 비밀 저장

- 입력 확인

- 스크립트 기술에 데이터 전달

  자세한 내용은 [애플리케이션 보안](../ide/securing-applications.md)을 참조하세요.

## <a name="downloaded-code-snippets"></a>다운로드된 코드 조각
 Visual Studio에 의해 설치된 IntelliSense 코드 조각 자체에는 보안 위험이 없습니다. 하지만 이 조각 때문에 애플리케이션에 보안 위험이 발생할 수 있습니다. 인터넷에서 다운로드된 조각은 다른 다운로드된 콘텐츠처럼 매우 주의해서 처리해야 합니다.

- 신뢰할 수 있는 사이트에서만 조각을 다운로드하고 최신 바이러스 소프트웨어를 사용하세요.

- 메모장 또는 Visual Studio의 XML 편집기에서 모든 다운로드된 조각 파일을 열고 설치하기 전에 주의해서 검토합니다. 다음 문제가 있는지 검색합니다.

  - 조각 코드를 실행하면 시스템이 손상될 수 있습니다. 실행하기 전에 소스 코드를 주의해서 읽으세요.

  - 조각 파일의 도움말 URL 블록에 악의적인 스크립트 파일을 실행하거나 공격적인 웹 사이트를 표시하는 URL이 포함되어 있을 수 있습니다.

  - 시스템의 임의 위치에서 로드되고 프로젝트에 자동으로 추가된 참조가 조각에 포함되어 있을 수 있습니다. 이러한 참조가 조각을 다운로드한 위치에서 컴퓨터에 다운로드되었을 수 있습니다. 나중에 이 조각이 참조에서 악성 코드를 실행하는 메서드를 호출할 수 있습니다. 이러한 공격을 방지하려면 조각 파일의 Imports 및 References 블록을 검토합니다.

## <a name="see-also"></a>관련 항목
 [Visual Basic IntelliSense 코드 조각](https://msdn.microsoft.com/library/ffdde4c9-8141-4906-b09b-15181357a643) [보안 응용 프로그램](../ide/securing-applications.md) [코드 조각](../ide/code-snippets.md)
