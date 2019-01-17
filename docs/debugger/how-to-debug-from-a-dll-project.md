---
title: '方法: DLL プロジェクトからデバッグ |Microsoft Docs'
ms.date: 10/10/2018
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
ms.openlocfilehash: 6dd7ec8938b8b7f94ba649affe48f170172f887b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854075"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>方法: Visual Studio で DLL プロジェクトからデバッグ (C#、C++、Visual Basic、 F#)

DLL プロジェクトをデバッグする方法の 1 つでは、DLL プロジェクトのプロパティで呼び出し元のアプリを指定します。 自体、DLL プロジェクトからデバッグを開始することができます。 このメソッドを使用するには、アプリは、構成するものと同じ場所に同じ DLL を呼び出す必要があります。 場合は、アプリを検索してさまざまなバージョンの DLL を読み込みます、そのバージョンには、ブレークポイントが含まれません。 その他の Dll のデバッグの方法では、次を参照してください。 [DLL のデバッグ プロジェクト](../debugger/debugging-dll-projects.md)します。
  
マネージ DLL を呼び出すネイティブ アプリ、管理対象アプリが、ネイティブ DLL を呼び出す、または、DLL と呼び出し元のアプリの両方をデバッグできます。 詳細については、「[方法 :混合モードでデバッグする](../debugger/how-to-debug-in-mixed-mode.md)   

ネイティブおよびマネージ DLL プロジェクトでは、呼び出し元のアプリを指定するためのさまざまな設定があります。 

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>呼び出し元のアプリをネイティブ DLL プロジェクトの指定します。  
  
1. C++ DLL プロジェクトを選択**ソリューション エクスプ ローラー**します。 選択、**プロパティ**アイコン、キーを押して**Alt**+**」と入力**、または右クリックし、選択**プロパティ**します。
   
1. **\<プロジェクト > プロパティ ページ** ダイアログ ボックスに、必ず、**構成**にウィンドウの上部にあるフィールドが設定されている**デバッグ**。 
   
1. 選択**構成プロパティ** > **デバッグ**します。  
   
1. **起動するデバッガー**一覧で、いずれかを選択**ローカル Windows デバッガー**または**リモート Windows デバッガー**します。  
   
1. **コマンド**または**リモート コマンド**ボックスに、呼び出し元のアプリのファイル名と完全修飾パスなどの追加、 *.exe*ファイル。
   
   ![[プロパティ] ウィンドウをデバッグ](../debugger/media/dbg-debugging-properties-dll.png "デバッグのプロパティ ウィンドウ")  
   
1. **[コマンド引数]** ボックスに、任意の必要なプログラム引数を追加します。  
   
1. **[OK]** を選択します。

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>マネージ DLL プロジェクトで呼び出し元のアプリを指定します。  
  
1. 選択、C#または Visual Basic DLL プロジェクトの **ソリューション エクスプ ローラー**します。 選択、**プロパティ**アイコン、キーを押して**Alt**+**」と入力**、または右クリックし、選択**プロパティ**します。
   
1. ウィンドウの上部にある **[構成]** フィールドが **[デバッグ]** に設定されていることを確認します。
   
1. **開始アクション**:
   
   - .NET Framework dll の場合、次のように選択します。**外部プログラムの開始**、呼び出し元のアプリの名前と完全修飾パスを追加します。
     
   - または、選択**URL でブラウザーを開始**しローカル ASP.NET アプリの URL を入力します。 
   
   - .NET Core の Dll を**デバッグ**プロパティ ページが異なる。 選択**実行可能ファイル**から、**起動**ドロップダウンで、し、呼び出し元のアプリでの名前と完全修飾パスを追加、**実行可能ファイル**フィールド。 
   
1. 必要なコマンドライン引数を追加、**コマンドライン引数**または**アプリケーション引数**フィールド。
   
   ![C#[プロパティ] ウィンドウをデバッグ](../debugger/media/dbg-debugging-properties-dll-csharp.png " C#デバッグのプロパティ ウィンドウ") 
   
1. 使用**ファイル** > **選択した項目の保存**または**Ctrl**+**S**変更を保存します。

## <a name="debug-from-the-dll-project"></a>DLL プロジェクトからデバッグします。  
 
1. DLL プロジェクトにブレークポイントを設定します。

1. DLL プロジェクトを右クリックし **スタートアップ プロジェクトとして設定**します。 

1. 確認、**ソリューション構成**にフィールドが設定されている**デバッグ**。 キーを押して**F5**、緑 をクリックして**開始**矢印または選択**デバッグ** > **デバッグの開始**。

デバッグしても、ブレークポイントがヒットしない場合、DLL を出力することを確認 (既定で、 *\<プロジェクト > \Debug*フォルダー) は、呼び出し元のアプリを呼び出している場所です。
  
## <a name="see-also"></a>関連項目  
 [DLL プロジェクトをデバッグする](../debugger/debugging-dll-projects.md)   
 [C# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)