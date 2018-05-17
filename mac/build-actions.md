---
title: ビルド アクション
description: この記事では、C# プロジェクトで使用できるさまざまなビルド アクションについて説明します。
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 889414d391a4a894879399317d782df58a8bacb3
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="build-actions"></a>ビルド アクション

Visual Studio for Mac プロジェクトのすべてのファイルにビルド アクションが含まれています。これは、ビルド中、ファイルに行われる処理を制御します。 設定するには、下の画像のように、ファイルをクリックし、**[ビルド アクション]** を選択ます。

![ソリューション エクスプローラーで [コンパイル] ビルド アクションを選択する](media/projects-and-solutions-image1.png)

C# プロジェクトの一般的ビルド アクションには次のようなものがあります。

* **なし** - このファイルはビルドに含まれていません。IDE から簡単にアクセスできるようにプロジェクトに追加されています。
* **コンパイル** - このファイルはソース ファイルとして C# コンパイラに渡されます。
* **EmbeddedResource** - このファイルはアセンブリに埋め込むリソースとして C# コンパイラに渡されます。 コンパイラに渡されたら、`System.Reflection` 名前空間を利用し、アセンブリからファイルを読むことができます。
* **コンテンツ** - ASP.NET プロジェクトの場合、展開時、このファイルはサイトの一部として追加されます。 Xamarin.iOS プロジェクトと Xamarin.Mac プロジェクトの場合、アプリ バンドルに含まれます。

ソリューション エクスプローラーでは、複数のファイルを選択できます。バンドル アクションを一度に複数のファイルに設定できます。

また、特定のプロジェクトのビルド アクションがあります。 たとえば、Xamarin.iOS プロジェクトには **BundleResource** ビルド アクションがあります。このアクションは、アプリ バンドルの一環としてファイルを追加します。 Xamarin.Android 固有のビルド アクションに関する詳細は、[ビルド プロセス](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) ガイドでご覧いただけます。