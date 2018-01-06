---
title: "方法: Visual Studio ソリューションの一部ではない実行可能ファイルのデバッグ |Microsoft ドキュメント"
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
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3ded5dfaec889e32bbf4c65f8e6a2335fd8c97a7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-an-executable-that-is-not-part-of-a-visual-studio-solution"></a>方法: Visual Studio ソリューションの一部ではない実行可能ファイルのデバッグ
実行可能ファイル (.exe ファイル) ではないをデバッグする場合もありますの一部、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]プロジェクト。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の外部で作成された実行可能ファイルや、他の人から受け取った実行可能ファイルなどがその例です。  
  
この問題を解決するには、通常、Visual Studio 外部の実行可能ファイルを起動して、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] デバッガーを使用してそのファイルにアタッチします。 詳細については、次を参照してください。[実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)です。  
  
アプリケーションへのアタッチは、一部を手動で実行する必要があります。この処理には数秒かかります。 アプリケーションの起動時に発生する問題をデバッグする場合は、このわずかな遅延のため、アタッチが役に立ちません。 また、ユーザー入力を待たず、すぐに終了するプログラムをデバッグする場合は、アタッチしている時間がないこともあります。 使用していれば[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]と[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]インストールされている場合、このようなプログラムの EXE プロジェクトを作成することができます。

> [!NOTE]
>  EXE プロジェクトをサポートしていないプログラミング言語もあります。

Visual Studio ソリューションの一部ではない実行可能ファイルをデバッグする際に利用できるデバッグ機能は限定されます、実行可能ファイルの実行中にアタッチする実行可能ファイルを追加するか、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ソリューションです。

- ソース コードがある場合は、そのソース コードを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] にインポートして、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で実行可能ファイルのデバッグ ビルドを作成するのが最適です。
- ソース コードがあるない場合、および実行可能ファイルなしでビルドされました[デバッグ情報](../debugger/how-to-set-debug-and-release-configurations.md)互換性のある形式で利用できるデバッグ機能は非常に限定します。 
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>既存の実行可能ファイルの EXE プロジェクトを作成するには  
  
1.  **ファイル** メニューのをクリックして**開く**選択**プロジェクト**です。  
  
2.  **プロジェクトを開く**ダイアログ ボックスで、ドロップダウン リストの次へ をクリック、**ファイル名**ボックス、および選択**すべてのプロジェクト ファイル**です。  
  
3.  実行可能ファイルを見つけてクリックして**OK**です。  

    これにより、実行可能ファイルを格納する一時的なソリューションが作成されます。

5.  などの実行コマンドを選択して、実行可能ファイルを開始します。**開始**、から、**デバッグ**メニュー。    
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Visual Studio ソリューションに実行可能ファイルをインポートするには  
  
1.  **ファイル** メニューのをポイント**プロジェクトの追加**、クリックして**既存のプロジェクト**です。  
  
2.  **既存プロジェクトの追加**ダイアログ ボックスで、ドロップダウン リストの次へ をクリック、**ファイル名**ボックス、および選択**すべてのプロジェクト ファイル**です。  
  
3.  目的の実行可能ファイルを見つけ、選択します。  
  
4.  **[OK]**をクリックします。  
  
5.  などの実行コマンドを選択して、実行可能ファイルを開始します。**開始**、から、**デバッグ**メニュー。    
  
## <a name="see-also"></a>参照  
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [DBG ファイル](http://msdn.microsoft.com/en-us/91e449e9-8b65-4123-960f-2107cd1f1cfd)