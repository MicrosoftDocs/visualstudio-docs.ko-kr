---
title: '방법: c # 프로젝트에 응용 프로그램 구성 파일 추가 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8417b5520dc9587fa3231a3bc459335d2a9896d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667527"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>방법: C# 프로젝트에 애플리케이션 구성 파일 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C# 프로젝트에 애플리케이션 구성 파일(app.config 파일)을 추가하면 공용 언어 런타임에서 어셈블리 파일을 찾고 로드하는 방법을 사용자 지정할 수 있습니다. 응용 프로그램 구성 파일에 대 한 자세한 내용은 [런타임에서 어셈블리를 찾는 방법](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34)을 참조 하세요.

> [!NOTE]
> Windows 스토어는를 지원 하지 않습니다 <xref:System.Configuration> . 따라서 스토어 앱에 app.config 템플릿이 포함 되어 있지 않습니다.

 프로젝트를 빌드할 때 개발 환경에서 자동으로 app.config 파일을 복사하고, 복사본의 파일 이름을 실행 파일과 일치하도록 변경한 다음, 복사본을 bin 디렉터리로 이동합니다.

### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>C # 프로젝트에 응용 프로그램 구성 파일을 추가 하려면

1. 메뉴 모음에서 **프로젝트**, **새 항목 추가**를 선택 합니다.

     **새 항목 추가** 대화 상자가 나타납니다.

2. **설치 됨**, **Visual c # 항목**을 차례로 확장 하 고 **응용 프로그램 구성 파일** 템플릿을 선택 합니다.

3. **이름** 텍스트 상자에서 이름을 입력하고 **추가** 단추를 선택합니다.

     app.config 이름이 지정 된 파일이 프로젝트에 추가 됩니다.

## <a name="see-also"></a>관련 항목
 [응용 프로그램 설정 관리 (.net)](../ide/managing-application-settings-dotnet.md) [구성 파일 스키마](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38) [앱 구성](https://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f) 방법: [c # 용 Visual Studio 개발 환경을 사용 하 여](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) [.NET Framework 버전을 대상으로 하도록 앱 구성](https://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717)