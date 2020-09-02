---
title: Visual Studio 2015 기능의 패키지 Guid | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C package GUIDs
ms.assetid: f56f0356-f3ac-48bc-9674-94259e29a4df
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8601b4f072c206ab19fdcb4a7248e79784af934a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546813"
---
# <a name="package-guids-of-visual-studio-features"></a>Visual Studio 기능의 패키지 GUID
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

격리 된 셸 응용 프로그램의 .pkgundef 파일에서 다음 Guid를 사용 하 여 응용 프로그램에서 특정 패키지를 제외할 수 있습니다.

## <a name="package-guids"></a>패키지 Guid

|기능 영역|원시 패키지 이름|패키지 GUID|
|------------------|----------------------|------------------|
|핵심 IDE|패키지 실행 취소|{1D76B2E0-F11B-11D2-AFC3-00105A9991EF}|
||Visual Studio 환경 패키지|{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}|
||Visual Studio 명령 정의 패키지|{44E07B02-29A5-11D3-B882-00C04F79F802}|
||패키지를 나열 하는 Visual Studio 디렉터리|{5010C52F-44AB-4051-8CE1-D36C20D989B4}|
||Visual Studio 공용 IDE 패키지|{6E87CFAD-6C05-4ADF-9CD7-3B7943875B7C}|
||Visual Studio 환경 메뉴 패키지|{715F10EB-9E99-11D2-BFC2-00C04F990235}|
||Visual Studio COM + 라이브러리 관리자 패키지|{ED8979BC-B02F-4dA9-A667-D3256C36220A}|
||Visual Studio 소스 제어 통합 패키지|{53544C4D-E3F8-4AA0-8195-8A8D16019423}|
||Visual Studio 솔루션 빌드 패키지|{282BD676-8B5B-11D0-8A34-00A0C91E2ACD}|
||텍스트 관리 패키지|F5E7E720-1401-11d1-883B-0000F87579D2|
||Visual Studio .Vssettings 패키지|{F74C5077-D848-4630-80C9-B00E68A1CA0C}|
|도움말|Visual Studio 도움말 패키지|{4A791146-19E4-11D3-B86B-00C04F79F802}|
|작업 목록, 오류 목록|ErrorListPackage|{4A9B7E50-AA16-11D0-A8C5-00A0C921A4D2}|
|클래스 개요|클래스 개요 패키지|{21AF45B0-FFA5-11D0-G63F-00A0C922E851}|
|도구 상자 컨트롤 설치 관리자|도구 상자 컨트롤 설치 관리자 패키지|{2C298B35-07DA-45F1-96A3-BE55D91C8d7A}|
|웹 프로젝트|VisualStudio|{349C5850-65DF-11DA-9384-00065B846F21}|
||Visual Web Developer 프로젝트 시스템 패키지|{39C9C826-8EF8-4079-8C95-428F5B1C323F}|
||Visual Web Developer 프로젝트 지 속성 패키지|{8FF02D1A-C177-4AC8-A62F-88FC6EA65F57}|
||Visual Web Developer 웹 마이그레이션 패키지|{C1DAB116-2D63-493A-B970-10D7DD0B476E}|
||Visual Web Developer 웹 패키지|{E7f851C8-6267-4794-B0FE-7BCAB6DACBB4}|
||Visual Web Developer 웹|{DC7F691A-91FC-4F7B-923E-FE829C3A18DC}|
|HTML 편집기|Visual Studio HTM 편집기 패키지|{1B437D20-F8FE-11D2-A6AE-00104BCC7269}|
||Visual Web Developer HTML 소스 편집기 패키지|{BFCC0C3C-6F87-4285-A6C8-BB616061800D}|
|CSS 편집기|Visual Studio CSS 편집 패키지|{A764E895-518D-11d2-9A89-00C04F79EFC3}|
|XML 편집기|Visual Studio XML 편집기 패키지|{87569308-4813-40A0-9CD0-D7A30838CA3F}|
|웹 브라우저|Visual Studio 웹 브라우저 패키지|{E8B06F41-6D01-11D2-AA7D-00C04F990343}|
||웹 응용 프로그램 프로젝트 팩터리, 브라우저 기능에서 보기|{349C5851-65DF-11DA-9384-00065B846F21}|
|바이너리 편집기|Visual Studio 이진 편집기 패키지|{5B98C2C0-CD7B-11D0-92DF-00A0C9138C45}|
|Windows Forms 디자이너|호스팅 패키지 Windows Forms 디자이너|{68939055-38E0-4D17-92CB-8909710D8178}|
||Windows Forms 디자이너 패키지|{7494682B-37A0-11D2-A273-00C04F8EF4FF}|
||Windows Forms 디자이너 리소스 패키지|{7B5D447B-0B12-41EA-A84E-C822034422D4}|
||응용 프로그램 구성 패키지 Windows Forms|{80C7728B-70A6-4528-8669-73E02D1B9C41}|
||ElementHost 디자이너 패키지|{7EAB3C71-59FF-4571-A5F3-643F255FC2E6}|
|디버거 UI|Visual Studio 디버거|{C9DD4A57-47FB-11D2-83E7-00C04F9902C1}|
|데이터베이스 도구|Visual Database Tools 패키지|{220A4C17-7E7C-4663-BCC-5E607C6543CD}|
||Visual Studio 데이터베이스 도구 디자이너|{EF828E39-70F5-4b8e-A3A0-4C0ECD28A69A}|
||Visual Studio 데이터 디자이너|{D6C919AA-1217-41E2-a13B-9B92E1866305}|
||Visual Studio 데이터 패키지|{E1AA7737-69BE-43d0-A425-E3097651E192}|
||Visual Studio 데이터 디자이너 확장성 패키지|{A8F602E2-40CE-4dAF-AE82-A457A91728B9}|
||Visual Studio 탐색기 및 디자이너 패키지|{8D8529D3-625D-4496-8354-3DAD630ECC1B}|
||Microsoft 보고서 디자이너|{F3A96850-E2AE-4E00-9278-8FE23F225A0D}|
|DSL 런타임|CommonModelingPackage|{D1091694-EA72-4BDD-8918-78324CC25448}|
||VisualStudio 템플릿|{A9696DE6-E209-414D-BBEC-A0506fb0E924}|
|SourceSafe 지원|Visual SourceSafe 공급자 패키지|{AA8EB8CD-7A51-11D0-92C3-00A0C9138C45}|
||Visual SourceSafe 공급자 스텁 패키지|{53544C4D-B03D-4209-A7D0-D9DD13A4019B}|
|WPF Designer|WPFFlavor.WPFPackage|{B3BAE735-386C-4030-8329-EF48EEDA4036}|
||XamlDesignerPackage|{512be089-83ec-4cc6-8483-cf16565ae209}|
||XamlLanguagePackage|{2ef1ec52-c8bf-4fe0-8ece-ba9c0d5d1603}|
||XamlDiagnosticsPackage|{8291c340-36b8-4c91-8c40-cce75398ff75}|
|코드 조각|Visual Studio Code 코드 조각 패키지|{0B680757-2C29-4531-80FA-535A5178AA98}|
|관리 언어 프로젝트 지원|Visual Studio 구성 요소 열거자|{588205E0-66e0-11D3-8600-00C04F6123B3}|
||Visual Studio 설정 및 프로젝트 디자이너 패키지|{67909B06-91E9-4F3E-AB50-495046BE9A9A}|
|템플릿 내보내기…|템플릿 패키지 내보내기|{F1E4CFCA-4573-4345-8718-7BDE2b1F0BE8}|

 일부 패키지는 다른 여러 기능에서 종속성을 사용 하므로 제거 하면 안 됩니다. 예를 들어 "핵심 IDE" 아래에 나열 된 항목은 제거 하면 안 됩니다.

 일부 기능은 완전히 제거할 수 없습니다. 예를 들어 **클래스 뷰** 및 관련 메뉴, 옵션 및 서비스를 제거 하기 위해 등록 취소할 수 있는 패키지가 없습니다. **클래스 뷰** 창은 다른 주요 IDE 기능도 제공 하는 Visual Studio 환경 패키지에서 제공 됩니다. **클래스 뷰**를 제거 하려는 경우에는 **찾기 및 바꾸기**, 환경 **옵션** 페이지, **명령 창**및 **출력** 창도 제거 해야 합니다.
