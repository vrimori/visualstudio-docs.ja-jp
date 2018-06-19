---
title: UWP アプリのリフレッシュ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: a45564f34fe0167821febb511a023c01f7c38358
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476281"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Visual Studio での UWP アプリをリフレッシュします。
  
 をデバッグしているし、JavaScript を使用して、を選択して、UWP アプリを更新中に、コードに変更を行うことができます、 **Windows アプリケーションの更新**のボタンでは、**デバッグ**ツールバー。 このボタンを選択すると、デバッガーを停止したり再起動したりせずにアプリが再度読み込まれます。 更新機能によって、HTML、CSS、および JavaScript コードを変更し、その結果をすばやく確認できます。 この機能は UWP アプリをサポートします。  
  
 更新では、アプリの状態は保持されません。また、アプリに対する次の変更は反映されません。  
  
-   パッケージ マニフェストに指定されたイメージの変更を含むパッケージ マニフェスト ファイルの変更。  
  
-   SDK 参照の追加や削除などの参照の変更、または Windows ランタイム コンポーネント (.winmd ファイル) の変更。  
  
-   .resjson ファイル内の文字列の変更などのリソースの変更。  
  
-   パス名の変更、新しいプロジェクト ファイル、または削除ファイルが発生するプロジェクト ファイルの変更。  
  
-   選択したデバッグ デバイスの変更などのプロジェクトおよび項目プロパティの変更、またはファイルのパッケージ操作の変更 ([プロパティ] ウィンドウ内)。  
  
> [!IMPORTANT]
>  参照やパッケージ マニフェストの変更など、上記の項目の変更を行った場合、HTML、CSS、および JavaScript のソース ファイルを更新するには、デバッガーを停止して再起動する必要があります。  
  
### <a name="to-refresh-an-app"></a>アプリを更新するには  
  
1.  UWP プロジェクトを Visual Studio で開いて、次のように選択します。**ローカル マシン**デバッグ ターゲットとして。
  
     ![デバッグ ターゲット リスト](../debugger/media/js_select_target.png "JS_Select_Target")  
  
3.  F5 キーを押して、アプリをデバッグ モードで実行します。  
  
4.  Visual Studio に切り替えます  
  
5.  UWP アプリのホーム ページの HTML の一部を編集します。
  
7.  クリックして、 **Windows アプリケーションの更新** ボタン、次のように表示されている:![アプリの Windows の更新ボタン](../debugger/media/js_refresh.png "JS_Refresh")です。 (または F4 キーを押します)。  
  
8.  アプリに切り替えます。 アプリが再度読み込まれ、更新された HTML がアプリを表示するために使用します。
  
## <a name="see-also"></a>関連項目  
 [クイック スタート: HTML および CSS のデバッグ](../debugger/quickstart-debug-html-and-css.md)