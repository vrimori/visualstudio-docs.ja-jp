---
title: "アプリの更新 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "デバッグ, 更新 (ページを) [Windows ストア アプリ]"
  - "DOM エクスプローラー, 更新 [Windows ストア アプリ]"
  - "JavaScript のデバッグ, 更新 (ページを) [Windows ストア アプリ]"
  - "更新 [Windows ストア アプリ]"
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# アプリの更新 (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Windows と Windows Phone に適用されます](../debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 デバッグ中にコードを変更し、**\[デバッグ\]** ツール バーの **\[Windows アプリケーションの更新\]** を選択することで、JavaScript を使用するストア アプリを更新できます。  このボタンを選択すると、デバッガーを停止したり再起動したりせずにアプリが再度読み込まれます。  更新機能によって、HTML、CSS、および JavaScript コードを変更し、その結果をすばやく確認できます。  この機能は、Windows ストア アプリと Windows Phone ストア アプリの両方でサポートされています。  
  
 更新では、アプリの状態は保持されません。また、アプリに対する次の変更は反映されません。  
  
-   パッケージ マニフェストに指定されたイメージの変更を含むパッケージ マニフェスト ファイルの変更。  
  
-   SDK 参照の追加や削除などの参照の変更、または Windows ランタイム コンポーネント \(.winmd ファイル\) の変更。  
  
-   .resjson ファイル内の文字列の変更などのリソースの変更。  
  
-   パス名の変更、新しいプロジェクト ファイル、または削除ファイルが発生するプロジェクト ファイルの変更。  
  
-   選択したデバッグ デバイスの変更などのプロジェクトおよび項目プロパティの変更、またはファイルのパッケージ操作の変更 \(\[プロパティ\] ウィンドウ内\)。  
  
> [!IMPORTANT]
>  参照やパッケージ マニフェストの変更など、上記の項目の変更を行った場合、HTML、CSS、および JavaScript のソース ファイルを更新するには、デバッガーを停止して再起動する必要があります。  
  
### アプリを更新するには  
  
1.  Visual Studio で、ナビゲーション アプリ プロジェクト テンプレートを使用して新しいプロジェクトを作成します。  
  
     Windows ストア アプリ、Windows Phone ストア アプリ、またはユニバーサル アプリのいずれでも作成できます。  
  
2.  Visual Studio でテンプレートを開いた状態で、デバッグ ターゲットを選択します。  
  
     Windows Phone プロジェクトが現在のスタートアップ プロジェクトである場合は、デバッグ ターゲットとして Windows Phone エミュレーターを選択します。  それ以外の場合は、**\[シミュレーター\]** または **\[ローカル コンピューター\]** を選択します。  
  
     ![デバッグ ターゲット リストを選択する](../debugger/media/js_select_target.png "JS\_Select\_Target")  
  
3.  F5 キーを押して、アプリをデバッグ モードで実行します。  
  
4.  Visual Studio に切り替えます   \(F12 キーを押します\)。  
  
5.  **ソリューション エクスプローラー** で、**\[ページ\]** の **\[ホーム\]** フォルダーから home.html を開きます。  
  
6.  次のページ タイトルのテキストを変更します。  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     次のように変更します。  
  
    ```html  
    Hello!  
    ```  
  
7.  **\[Windows アプリケーションの更新\]** ボタン \(![&#91;Windows アプリケーションの更新&#93; ボタン](../debugger/media/js_refresh.png "JS\_Refresh")\) をクリックします   \(または F4 キーを押します\)。  
  
8.  アプリに切り替えます。  デバッガーを再起動せずにアプリが再度読み込まれ、新しいページ タイトルが表示されます。  
  
## 参照  
 [クイック スタート: HTML および CSS のデバッグ](../debugger/quickstart-debug-html-and-css.md)