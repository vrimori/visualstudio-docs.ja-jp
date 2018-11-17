---
title: アプリの更新 (JavaScript) |Microsoft Docs
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
- JavaScript debugging, refreshing pages [Windows Store apps]
- debugging, refreshing pages [Windows Store apps]
- DOM Explorer, Refresh [Windows Store apps]
- Refresh [Windows Store apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1905d48e79567684da6215b419c348b32721e0e3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722898"
---
# <a name="refresh-an-app-javascript"></a>アプリの更新 (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows および Windows Phone に適用されます] (../Image/windows_and_phone_content.png"windows_and_phone_content")  
  
 デバッグ中から選択して、JavaScript を使用するストア アプリを更新中に、コードに変更を行うことができます、**更新の Windows アプリ**のボタンでは、**デバッグ**ツールバー。 このボタンを選択すると、デバッガーを停止したり再起動したりせずにアプリが再度読み込まれます。 更新機能によって、HTML、CSS、および JavaScript コードを変更し、その結果をすばやく確認できます。 この機能は、Windows ストア アプリと Windows Phone ストア アプリの両方でサポートされています。  
  
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
  
     Windows ストア アプリ、Windows Phone ストア アプリ、またはユニバーサル アプリのいずれでも作成できます。  
  
2.  Visual Studio でテンプレートを開いた状態で、デバッグ ターゲットを選択します。  
  
     Windows Phone プロジェクトが現在のスタートアップ プロジェクトである場合は、デバッグ ターゲットとして Windows Phone エミュレーターを選択します。 それ以外の場合、選択**シミュレーター**または**ローカル マシン**します。  
  
     ![デバッグ ターゲット リスト](../debugger/media/js-select-target.png "JS_Select_Target")  
  
3.  F5 キーを押して、アプリをデバッグ モードで実行します。  
  
4.  Visual Studio に切り替えます  (F12 キーを押します)。  
  
5.  **ソリューション エクスプ ローラー**の**ページ** > **ホーム**フォルダーから home.html を開きます。  
  
6.  次のページ タイトルのテキストを変更します。  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     次のように変更します。  
  
    ```html  
    Hello!  
    ```  
  
7.  をクリックして、**更新の Windows アプリ**のように、ボタン:![更新の Windows アプリのボタン](../debugger/media/js-refresh.png "JS_Refresh")します。 (または F4 キーを押します)。  
  
8.  アプリに切り替えます。 デバッガーを再起動せずにアプリが再度読み込まれ、新しいページ タイトルが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [クイック スタート: HTML および CSS のデバッグ](../debugger/quickstart-debug-html-and-css.md)



