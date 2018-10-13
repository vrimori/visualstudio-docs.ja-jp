---
title: Web プロジェクトのプロパティ ページ設定 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a472e134869ff48a21480ede42f330d968262d38
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49179986"
---
# <a name="property-pages-settings-for-web-projects"></a>Web プロジェクトのプロパティ ページ設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Web サイトのデバッグ構成のプロパティの設定を変更することができます、**プロパティ ページ** ダイアログ ボックスで説明したよう[デバッグ構成とリリース構成](../debugger/how-to-set-debug-and-release-configurations.md)します。 次の表は、デバッガー関連の設定を検索する場所を示して、**プロパティ ページ** ダイアログ ボックス。  
  
### <a name="configuration-properties-folder-start-options-category"></a>[構成プロパティ] フォルダー ([開始オプション] カテゴリ)  
  
|**設定**|**説明**|  
|-----------------|---------------------|  
|**開始アクション**|アプリケーションの起動に関するオプション グループの見出しです。|  
|**現在のページを使用して、**|デバッグの開始点として現在のページを指定します。|  
|**特定のページ:**|デバッグを開始する Web ページを指定します。|  
|**外部プログラムを開始します。**|デバッグするプログラムを起動するコマンドを指定します。|  
|**コマンドライン引数:**|上で指定したコマンドの引数を指定します。|  
|**作業ディレクトリ:**|デバッグするプログラムの作業ディレクトリを指定します。 [!INCLUDE[csprcs](../includes/csprcs-md.md)] では、作業ディレクトリはアプリケーションが起動されるディレクトリであり、既定では \bin\debug です。|  
|**URL を開始します。**|デバッグする Web アプリケーションの場所を指定します。|  
|**[ページを開かずに外部アプリケーションからの要求を待つ]外部アプリケーションからの要求を待つ**|外部のアプリケーションからの要求を待つように指示します。 このオプションは、Internet Explorer やその他のアプリケーションを起動しません。 アプリケーションから呼び出されたときにデバッグの準備をするだけです。|  
|**サーバー**|使用するサーバーに関するオプション グループの見出しです。|  
|**既定の Web サーバーを使用します。**|既定の Web サーバーを使用するように指定します。|  
|**カスタム サーバーを使用します。**|サーバーとして使用するベース URL を入力できます。|  
|**デバッガー**|実行するデバッグの種類に関するオプション グループの見出しです。|  
|**ASP.NET のデバッグ**|[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 開発プラットフォーム用に記述されたサーバー ページのデバッグを有効にします。 URL を指定する必要があります**URL の開始**します。|  
|**ネイティブ コードのデバッグ**|マネージド アプリケーションからネイティブ (アンマネージド) Win32 コードの呼び出しをデバッグできます。|  
|**SQL Server のデバッグ**|SQL Server データベース オブジェクトのデバッグを許可します。|  
|**Silverlight デバッグ**|Silverlight コンポーネントをデバッグできます。|  
  
## <a name="see-also"></a>関連項目  
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)



