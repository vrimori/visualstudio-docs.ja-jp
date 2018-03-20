---
title: "アプリ リソースの管理"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 61EAAB8F-3C32-4574-924F-CFC616604089
ms.openlocfilehash: 95aa6abeb5a64158fe0ef0ed2b64392108248523
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="managing-app-resources"></a>アプリ リソースの管理

アプリケーションには、画像、テキスト ファイル、オーディオ ファイルなどのアプリ リソース ファイルが必要ですが、これらはアプリケーションと共にコンパイルされません。 Visual Studio for Mac でサポートされる各プラットフォームでは、これらのリソースは、以下のガイドで説明するように、異なる方法で処理されます。

## <a name="xamarinforms"></a>Xamarin.Forms

Xamarin.Forms コードは複数のプラットフォームで実行されます。各プラットフォームには独自のファイル システムがあり、ファイルへの読み書き方法は各ファイル システムによって指示されます。 Xamarin.Forms では、各プラットフォームでネイティブのファイル API を使用するか、埋め込みリソースとしてファイルを追加することによって、アプリ リソースを管理できます。

* [イメージの処理](https://developer.xamarin.com/guides/xamarin-forms/user-interface/images/)
* [ファイルの処理]( https://developer.xamarin.com/guides/xamarin-forms/application-fundamentals/files/)


## <a name="xamarinios"></a>Xamarin.iOS

* [リソースの処理](https://developer.xamarin.com/guides/ios/application_fundamentals/working_with_resources/)
* [イメージの処理](https://developer.xamarin.com/guides/ios/application_fundamentals/working_with_images/)
* [ファイル システムの処理](https://developer.xamarin.com/guides/ios/application_fundamentals/working_with_the_file_system/)


## <a name="xamarinandroid"></a>Xamarin.Android

* [Android リソース](https://developer.xamarin.com/guides/android/application_fundamentals/resources_in_android/)

## <a name="xamarinmac"></a>Xamarin.Mac

* [イメージの処理](https://developer.xamarin.com/guides/mac/application_fundamentals/working-with-images/)


