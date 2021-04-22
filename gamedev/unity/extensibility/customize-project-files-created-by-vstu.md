---
title: VSTU에서 만든 프로젝트 파일 사용자 지정 | Microsoft Docs
description: VSTU(Visual Studio Tools for Unity)에서 생성한 프로젝트 파일을 사용자 지정하는 방법을 알아봅니다. C# 코드 예제를 검토합니다.
ms.custom: ''
ms.date: 04/19/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a4a5973863877db2d071f9be8d4689928b21a689
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879319"
---
# <a name="customize-project-files-created-by-vstu"></a>VSTU에서 만든 프로젝트 파일 사용자 지정
Unity는 프로젝트 파일을 생성 하는 동안 콜백을 제공 합니다. 를 `OnGeneratedSlnSolution` `OnGeneratedCSProject` 사용 하 여 및 메서드를 구현 하 여 [`AssetPostprocessor`](https://docs.unity3d.com/ScriptReference/AssetPostprocessor.html) 프로젝트 또는 솔루션 파일을 다시 생성할 때마다 수정 합니다.

## <a name="demonstrates"></a>데모
Visual Studio Tools for Unity에서 생성한 Visual Studio 프로젝트 파일을 사용자 지정하는 방법

## <a name="example"></a>예제

```csharp
using System;
using UnityEditor;
using UnityEngine;

public class ProjectFilePostprocessor : AssetPostprocessor
{
  public static string OnGeneratedSlnSolution(string path, string content)
  {
    // TODO: process solution content
    return content;
  }

  public static string OnGeneratedCSProject(string path, string content)
  {
    // TODO: process project content
    return content;
  }
}
```
