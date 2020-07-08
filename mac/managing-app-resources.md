---
title: 앱 리소스 관리
description: 이 문서는 Mac용 Visual Studio에서 다양한 플랫폼을 위한 앱 리소스를 관리하는 방법을 설명하는 여러 가이드로 연결됩니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 61EAAB8F-3C32-4574-924F-CFC616604089
ms.topic: overview
ms.openlocfilehash: 987a337941ba2a180045e64c5ba26dfd54284bec
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85938375"
---
# <a name="managing-app-resources"></a>앱 리소스 관리

이미지, 텍스트 파일 및 오디오 파일과 같은 앱 리소스 파일은 애플리케이션에 필요하지만 애플리케이션에서 컴파일되지 않습니다. Mac용 Visual Studio에서 지원되는 플랫폼은 다음 가이드에 설명된 대로 이러한 리소스를 각기 다른 방식으로 처리합니다.

## <a name="xamarinforms"></a>Xamarin.Forms

Xamarin.Forms 코드는 여러 플랫폼에서 실행됩니다. 각 플랫폼에는 고유한 파일 시스템이 있고, 각 파일 시스템은 파일을 읽고 쓰는 방법을 지정합니다. Xamarin.Forms에서는 각 플랫폼에서 네이티브 파일 API를 사용하거나 포함된 리소스로 파일을 추가하여 앱 리소스를 관리할 수 있습니다.

* [이미지 작업](https://developer.xamarin.com/guides/xamarin-forms/user-interface/images/)
* [파일 작업]( https://developer.xamarin.com/guides/xamarin-forms/application-fundamentals/files/)

## <a name="xamarinios"></a>Xamarin.iOS

* [리소스 작업](https://developer.xamarin.com/guides/ios/application_fundamentals/working_with_resources/)
* [이미지 작업](https://developer.xamarin.com/guides/ios/application_fundamentals/working_with_images/)
* [파일 시스템 작업](https://developer.xamarin.com/guides/ios/application_fundamentals/working_with_the_file_system/)

## <a name="xamarinandroid"></a>Xamarin.Android

* [Android 리소스](https://developer.xamarin.com/guides/android/application_fundamentals/resources_in_android/)

## <a name="xamarinmac"></a>Xamarin.Mac

* [이미지 작업](https://developer.xamarin.com/guides/mac/application_fundamentals/working-with-images/)

## <a name="see-also"></a>참고 항목

- [애플리케이션 리소스 관리(Windows의 Visual Studio)](/visualstudio/ide/managing-application-resources-dotnet)