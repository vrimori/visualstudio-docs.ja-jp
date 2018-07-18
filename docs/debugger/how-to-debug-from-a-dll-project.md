---
title: '方法: DLL プロジェクトからデバッグ |Microsoft ドキュメント'
ms.custom: ''
ms.date: 05/24/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63581cee8816e72492a67a0981a9077b9fec2935
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475812"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio"></a>方法: Visual Studio で、DLL プロジェクトからデバッグ
DLL プロジェクトをデバッグする方法の 1 つは、DLL プロジェクトのプロジェクト プロパティで呼び出し元のアプリケーションを指定して、DLL プロジェクトからデバッグを開始する、します。 このメソッドを使用するには、アプリケーションが DLL を呼び出す必要があります、DLL は、アプリケーションがそれを検索する場所にする必要があります (それ以外の場合、アプリケーションを別のバージョンの DLL を検索して代わりに、読み込む可能性があり、、ブレークポイントをヒットしません)。 他の Dll のデバッグの方法では、次を参照してください。 [DLL プロジェクトのデバッグ](../debugger/debugging-dll-projects.md)です。
  
マネージ DLL がネイティブ コードによって呼び出され、両方をデバッグする場合は、このプロジェクトのプロパティで指定できます。 詳細については、「 [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md)」を参照してください。   

C++ のプロパティ ページは、C# と Visual Basic のプロパティ ページとレイアウトおよび内容が異なります。 
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>C++ プロジェクトで呼び出し元のアプリケーションを指定するには  
  
1.  プロジェクト ノードを右クリックし、**ソリューション エクスプ ローラー**選択**プロパティ**です。  
  
2.  確認して、**構成**にウィンドウの上部にあるフィールドが設定されている**デバッグ**です。 

    A**デバッグ**構成はこのメソッドに必要です。 
  
3.  移動して**構成プロパティ > デバッグ**です。  
  
4.  **起動するデバッガー**一覧で、選択**ローカル Windows デバッガー**または**リモート Windows デバッガー**です。  
  
5.  **コマンド**または**リモート コマンド**ボックスで、呼び出し元のアプリケーション (.exe ファイル) などの完全修飾パス名を追加します。

    ![[プロパティ] ウィンドウをデバッグ](../debugger/media/dbg-debugging-properties-dll.png "DebuggingPropertiesWindow")  
  
6.  必要なプログラム引数を追加、**コマンド引数**ボックス。  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>C# または Visual Basic のプロジェクトで呼び出し元のアプリケーションを指定するには  
  
1.  プロジェクト ノードを右クリックし、**ソリューション エクスプ ローラー**選択**プロパティ**、し、、**デバッグ**タブです。

2.  確認して、**構成**にウィンドウの上部にあるフィールドが設定されている**デバッグ**です。

3.  (.NET framework)選択**外部プログラムの開始**、呼び出し元のアプリケーションの完全修飾パス名を追加します。

4.  (.NET core)選択**実行可能ファイル**から、**起動**一覧、および呼び出し元のアプリケーションの完全修飾パス名を追加、**実行可能ファイル**フィールドです。 
  
     外部プログラムのコマンドライン引数を追加する必要がある場合にそれらを追加、**コマンドライン引数**(または**アプリケーション引数**) フィールドです。

    ![[プロパティ] ウィンドウをデバッグ](../debugger/media/dbg-debugging-properties-dll-csharp.png "DebuggingPropertiesWindow") 

5.  する必要がある場合は、URL としてアプリケーションも呼び出すことができます。 ローカル ASP.NET アプリケーションが使用するマネージ DLL をデバッグする場合は、この手順を実行します。  
  
     **開始動作**、select、 **URL でブラウザーを開始:** ラジオ ボタンをクリックし、URL を入力します。
  
### <a name="to-start-debugging-from-the-dll-project"></a>DLL プロジェクトからデバッグを開始するには  
  
1.  DLL プロジェクトにブレークポイントを設定します。 

2.  DLL プロジェクトを右クリックして選択**スタートアップ プロジェクトとして設定**です。 

    (また、ことを確認、**ソリューション構成**フィールドが設定されている**デバッグ**)。   
  
3.  デバッグを開始 (f5 キーを押して、緑色の矢印をクリックしてまたはクリックして**デバッグ > [デバッグ開始]**)。

    DLL 内のブレークポイントがヒットします。 ブレークポイントにヒットすることはない場合は、DLL が出力を確認してください (既定では、 **project\Debug**フォルダー) の場所には、呼び出し元のアプリケーションが参照することです。
  
## <a name="see-also"></a>関連項目  
 [DLL プロジェクトのデバッグ](../debugger/debugging-dll-projects.md)   
 [C# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)