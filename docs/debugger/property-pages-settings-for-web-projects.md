---
title: Web プロジェクトのプロパティの設定 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09aeb8d97c1caf3eca067cd7992eb96c9d7ef7c1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892664"
---
# <a name="property-pages-settings-for-web-projects"></a>Web プロジェクトのプロパティ ページ設定
「[デバッグ構成とリリース構成](../debugger/how-to-set-debug-and-release-configurations.md)」で説明したように、Web サイト デバッグ構成のプロパティ設定は **[プロパティ ページ]** ダイアログ ボックスで変更できます。 次の表は、**[プロパティ ページ]** ダイアログ ボックスのデバッガー関連の設定の場所を示しています。  
  
### <a name="configuration-properties-folder-start-options-category"></a>[構成プロパティ] フォルダー ([開始オプション] カテゴリ)  
  
| **設定** | **説明** |
| - | - |
| **開始動作** | アプリケーションの起動に関するオプション グループの見出しです。 |
| **現在のページを使用する** | デバッグの開始点として現在のページを指定します。 |
| **ページを指定する** | デバッグを開始する Web ページを指定します。 |
| **外部プログラムの開始:** | デバッグするプログラムを起動するコマンドを指定します。 |
| **コマンド ライン引数:** | 上で指定したコマンドの引数を指定します。 |
| **作業ディレクトリ:** | デバッグするプログラムの作業ディレクトリを指定します。 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] では、作業ディレクトリはアプリケーションが起動されるディレクトリであり、既定では \bin\debug です。 |
| **URL の開始** | デバッグする Web アプリケーションの場所を指定します。 |
| **[ページを開かずに外部アプリケーションからの要求を待つ]** | 外部のアプリケーションからの要求を待つように指示します。 このオプションは、Internet Explorer やその他のアプリケーションを起動しません。 アプリケーションから呼び出されたときにデバッグの準備をするだけです。 |
| **サーバー** | 使用するサーバーに関するオプション グループの見出しです。 |
| **既定 Web サーバーを使用する** | 既定の Web サーバーを使用するように指定します。 |
| **カスタム サーバーを使用する** | サーバーとして使用するベース URL を入力できます。 |
| **デバッガー** | 実行するデバッグの種類に関するオプション グループの見出しです。 |
| **ASP.NET デバッグ** | [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 開発プラットフォーム用に記述されたサーバー ページのデバッグを有効にします。 **[URL の開始]** に URL を指定する必要があります。 |
| **ネイティブ コード デバッグ** | マネージド アプリケーションからネイティブ (アンマネージド) Win32 コードの呼び出しをデバッグできます。 |
| **SQL Server デバッグ** | SQL Server データベース オブジェクトのデバッグを許可します。 |
| **Silverlight デバッグ** | Silverlight コンポーネントをデバッグできます。 |
  
## <a name="see-also"></a>「  
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)