---
title: 방법 - Windows 기호 정보 참조 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 88df7c676e6dbd95704716eb8a361f2fce7f66d4
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328828"
---
# <a name="how-to-reference-windows-symbol-information"></a>방법: Windows 기호 정보 참조
Visual Studio 프로파일링 도구는 기호 파일(.*pdb*)을 사용하여 프로그램 바이너리의 함수 이름과 같은 기호 이름을 확인합니다. 로컬 컴퓨터에 설치된 Windows 버전에 대한 올바른 .*pdb* 파일을 자동으로 다운로드하고 업데이트하려면 다음 단계를 수행합니다.

> [!NOTE]
> 이 설정은 기존 보고서에 영향을 미치지 않습니다. 기호 서버를 지정한 후 만들어진 보고서에만 기호 정보가 포함됩니다.

 자세한 내용은 [기호 파일(.*pdb*) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요.

### <a name="to-use-the-microsoft-symbol-server"></a>Microsoft 기호 서버를 사용하려면

1. 기호 파일 정보가 포함된 폴더를 만듭니다(예: C:\SymbolCache).

2. **도구** 메뉴에서 **옵션**을 클릭합니다.

     **옵션** 대화 상자가 표시됩니다.

3. **디버깅** 트리를 확장하고 **기호**를 클릭합니다.

4. **기호 파일(.pdb) 위치**에서 **Microsoft 기호 서버**를 선택합니다.

5. **기호 서버에서 이 디렉터리로 기호 캐시**에서 다음과 같이 1단계에서 만든 폴더의 경로를 입력합니다.

     **C:\SymbolCache**

     줄임표 단추( **...** )를 클릭한 후 **폴더 찾아보기** 대화 상자에서 디렉터리를 선택할 수도 있습니다.

## <a name="see-also"></a>참조
- [성능 세션 구성](../profiling/configuring-performance-sessions.md)
- [방법: 기호 정보 직렬화](../profiling/how-to-serialize-symbol-information.md)
