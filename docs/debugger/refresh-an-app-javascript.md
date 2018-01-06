---
title: "UWP または Windows 8.1 アプリの更新 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 636f88313d53625e5bb778ffe7bebc8f891ed4bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="refresh-a-uwp-or-windows-81-app"></a>UWP または Windows 8.1 アプリを更新します。
![Windows と Windows Phone に適用](../debugger/media/windows_and_phone_content.png "windows_and_phone_content")  
  
 をデバッグしているし、JavaScript を使用して、を選択して、UWP アプリを更新中に、コードに変更を行うことができます、 **Windows アプリケーションの更新**のボタンでは、**デバッグ**ツールバー。 このボタンを選択すると、デバッガーを停止したり再起動したりせずにアプリが再度読み込まれます。 更新機能によって、HTML、CSS、および JavaScript コードを変更し、その結果をすばやく確認できます。 この機能は、UWP と Windows 8.1 アプリではサポートされます。  
  
 更新では、アプリの状態は保持されません。また、アプリに対する次の変更は反映されません。  
  
-   パッケージ マニフェストに指定されたイメージの変更を含むパッケージ マニフェスト ファイルの変更。  
  
-   SDK 参照の追加や削除などの参照の変更、または Windows ランタイム コンポーネント (.winmd ファイル) の変更。  
  
-   .resjson ファイル内の文字列の変更などのリソースの変更。  
  
-   パス名の変更、新しいプロジェクト ファイル、または削除ファイルが発生するプロジェクト ファイルの変更。  
  
-   選択したデバッグ デバイスの変更などのプロジェクトおよび項目プロパティの変更、またはファイルのパッケージ操作の変更 ([プロパティ] ウィンドウ内)。  
  
> [!IMPORTANT]
>  参照やパッケージ マニフェストの変更など、上記の項目の変更を行った場合、HTML、CSS、および JavaScript のソース ファイルを更新するには、デバッガーを停止して再起動する必要があります。  
  
### <a name="to-refresh-an-app"></a>アプリを更新するには  
  
1.  Visual Studio で、ナビゲーション アプリ プロジェクト テンプレートを使用して新しいプロジェクトを作成します。  
  
     これには、UWP アプリまたは Windows 8.1 アプリを指定できます。  
  
2.  Visual Studio でテンプレートを開いた状態で、デバッグ ターゲットを選択します。  
  
     Windows Phone プロジェクトが現在のスタートアップ プロジェクトである場合は、デバッグ ターゲットとして Windows Phone エミュレーターを選択します。 それ以外の場合、選択**シミュレーター**または**ローカル マシン**です。  
  
     ![デバッグ ターゲット リスト](../debugger/media/js_select_target.png "JS_Select_Target")  
  
3.  F5 キーを押して、アプリをデバッグ モードで実行します。  
  
4.  Visual Studio に切り替えます  (F12 キーを押します)。  
  
5.  **ソリューション エクスプ ローラー**で、**ページ** > **ホーム**フォルダーから home.html を開きます。  
  
6.  次のページ タイトルのテキストを変更します。  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     次のように変更します。  
  
    ```html  
    Hello!  
    ```  
  
7.  クリックして、 **Windows アプリケーションの更新** ボタン、次のように表示されている:![アプリの Windows の更新ボタン](../debugger/media/js_refresh.png "JS_Refresh")です。 (または F4 キーを押します)。  
  
8.  アプリに切り替えます。 デバッガーを再起動せずにアプリが再度読み込まれ、新しいページ タイトルが表示されます。  
  
## <a name="see-also"></a>参照  
 [クイック スタート: HTML および CSS のデバッグ](../debugger/quickstart-debug-html-and-css.md)