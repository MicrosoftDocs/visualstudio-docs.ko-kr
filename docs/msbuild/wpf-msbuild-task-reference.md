---
title: WPF MSBuild 작업 참조 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84aeae06a5440bfc82eb9590919800ebcdd425d5
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578182"
---
# <a name="wpf-msbuild-task-reference"></a>WPF MSBuild 작업 참조
WPF(Windows Presentation Foundation) 빌드 프로세스는 태그를 컴파일하고 리소스를 처리하는 작업 등을 포함한 추가적인 빌드 작업 집합을 사용하여 Microsoft Build Engine(MSBuild)을 확장합니다.

## <a name="in-this-section"></a>단원 내용
- [FileClassifier](../msbuild/fileclassifier-task.md)

 소스 리소스 집합을 어셈블리에 포함될 항목으로 분류합니다. 리소스를 지역화할 수 없는 경우 주 애플리케이션 어셈블리에 포함되고, 그렇지 않으면 위성 어셈블리에 포함합니다.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 프로젝트에서 하나 이상의 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 페이지가 해당 프로젝트에서 로컬로 선언된 형식을 참조할 경우 어셈블리를 생성합니다. 생성된 어셈블리는 빌드 프로세스가 완료된 후 또는 빌드 프로세스가 실패하는 경우에 제거됩니다.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 현재 [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] 런타임의 디렉터리를 반환합니다.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 지역화할 수 없는 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 프로젝트 파일을 컴파일된 이진 형식 파일로 변환합니다.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 같은 프로젝트의 형식을 참조하는 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 파일에 대해 두 번째 패스 태그 컴파일을 수행합니다.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 하나 이상의 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 이진 형식 파일에 대한 지역화 특성과 주석을 전체 어셈블리에 대한 단일 파일로 병합합니다.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 하나 이상의 리소스( *.jpg*, *.ico*, *.bmp*, 이진 형식의 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 및 기타 확장 형식)를 *.resources* 파일에 포함합니다.

- [UidManager](../msbuild/uidmanager-task.md)

 소스 [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] 파일에 포함된 모든 [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] 요소를 지역화하기 위해 UID(고유 식별자)를 확인, 업데이트 또는 제거합니다.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] 프로젝트를 빌드할 때 애플리케이션 매니페스트( *\<projectname.exe.manifest*)에 **\<hostInBrowser /&gt;** 요소를 추가하기 위해 실행합니다.

## <a name="see-also"></a>참조
- [MSBuild](../msbuild/msbuild.md)