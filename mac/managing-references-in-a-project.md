---
title: "プロジェクト内の参照の管理"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 30f6c99c6ac827b7da94fd228a7034e9ce0b0fac
ms.contentlocale: ja-jp
ms.lasthandoff: 08/11/2017

---

# <a name="managing-references-in-a-project"></a>プロジェクト内の参照の管理

Visual Studio for Mac には、プロジェクトに参照を追加する方法が 3 つあります。

![プロジェクト参照](media/projects-and-solutions-image10.png)

これらの数値は、次のとおりです。

* 参照
* NuGet (パッケージ フォルダーで追加)
* コンポーネント

さらに、Web 参照とネイティブ参照は任意のプロジェクトに追加することもできます。

## <a name="assembly-references"></a>アセンブリ参照

Xamarin 内の各フレームワークには、十数個のアセンブリが付属しています。 これらのアセンブリ パッケージの一部は、プロジェクトの既定では参照されていません。 

プロジェクトで参照するパッケージを編集するには、_[参照の編集]_ ダイアログを使用します。このダイアログを表示するには、[参照] フォルダーをダブルクリックするか、コンテキスト メニュー操作で [参照の編集] を選択します。

![アセンブリの参照ダイアログ](media/projects-and-solutions-image11.png)

各 Xamarin フレームワークで使用できるアセンブリについては、「[Available Assemblies](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/)」(使用可能なアセンブリ) ガイドを参照してください。

## <a name="nuget"></a>NuGet

NuGet は、.NET 開発用の最も人気のあるパッケージ マネージャーです。 Visual Studio for Mac は NuGet をサポートしているので、パッケージを検索してプロジェクトに追加することができます。

追加するには、Solution Pad で **[パッケージ]** フォルダーを右クリックし、[パッケージの追加] を選択します。

NuGet パッケージの使用方法については、「[Including a NuGet package in your Project](~/nuget-walkthrough.md)」(プロジェクトに NuGet パッケージを含める) チュートリアルを参照してください。

