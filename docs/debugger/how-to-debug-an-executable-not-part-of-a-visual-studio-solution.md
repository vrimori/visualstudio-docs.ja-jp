---
title: Visual Studio ソリューションに含まれていないアプリをデバッグします。
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/19/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8c408ca42f82c0419c6570068e2a83e97f2371e9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066614"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Visual Studio ソリューションに含まれていないアプリのデバッグ (C++、 C#、Visual Basic、 F#)

アプリをデバッグすることがあります (*.exe*ファイル)、Visual Studio ソリューションの一部ではないです。 誰かが、Visual Studio の外部でアプリを作成した可能性があります。 または別の場所からアプリを取得します。 

Visual Studio に存在しないアプリをデバッグする通常の方法が、Visual Studio の外部からアプリを起動しを使用して接続し、**プロセスにアタッチ**Visual Studio デバッガーでします。 詳細については、次を参照してください。[実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)します。  
  
アプリにアタッチするには、数秒かかる手動の手順が必要です。 この遅延のためのアタッチ、起動時の問題をデバッグすることはできませんまたはアプリ ユーザーを待ちませんを入力し、すぐに終了します。 

このような場合は、アプリでは、Visual Studio の EXE プロジェクトを作成または既存のインポートC#、Visual Basic、または C++ ソリューション。 EXE プロジェクトをサポートしていないプログラミング言語もあります。 

>[!IMPORTANT]
>Visual Studio に組み込まれていないアプリのデバッグ機能は、アプリにアタッチするか、Visual Studio ソリューションに追加するかどうか、制限されます。 
>
>ソース コードがある場合は、最良のアプローチは、Visual Studio プロジェクトにコードをインポートするのには。 次に、アプリのデバッグ ビルドを実行します。
>
>かどうか、ソース コードがないし、アプリが見つからない[デバッグ情報](../debugger/how-to-set-debug-and-release-configurations.md)互換の形式で使用可能なデバッグ機能はごくわずかです。 

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>既存のアプリの新しい EXE プロジェクトを作成するには  
   
1. Visual Studio で、次のように選択します。**ファイル** > **オープン** > **プロジェクト**します。  
   
1. **プロジェクトを開く**ダイアログ ボックスで、**すべてのプロジェクト ファイル**選択されていない場合、ドロップダウンの横に、**ファイル名**します。  
   
1. 移動し、 *.exe*ファイル、それを選択し、**オープン**します。  
   
   新しい一時的な Visual Studio ソリューションにファイルが表示されます。

1. このような実行コマンドを選択して、アプリのデバッグを開始**デバッグの開始**から、**デバッグ**メニュー。    
  
### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>既存の Visual Studio ソリューションにアプリをインポートするには  
  
1.  C++、 C#、Visual Studio で開いている Visual Basic ソリューションを選択または**ファイル** > **追加** > **既存のプロジェクト**。  
  
1. **プロジェクトを開く**ダイアログ ボックスで、**すべてのプロジェクト ファイル**選択されていない場合、ドロップダウンの横に、**ファイル名**します。  
   
1. 移動し、 *.exe*ファイル、それを選択し、**オープン**します。  
   
   新しいプロジェクトを現在のソリューションとして、ファイルが表示されます。  
   
1. 新しいファイルが選択状態などの実行コマンドを選択して、アプリのデバッグを開始**デバッグの開始**から、**デバッグ**メニュー。    
  
### <a name="see-also"></a>関連項目  
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [DBG ファイル](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))