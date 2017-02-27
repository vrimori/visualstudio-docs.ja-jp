---
title: "方法 : Visual Studio ソリューションに含まれていない実行可能ファイルをデバッグする | Microsoft Docs"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "デバッグ [Visual Studio], 実行可能ファイル"
  - "実行可能ファイル, デバッグ (プロジェクト外部での)"
  - "実行可能ファイル, インポート"
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# 方法 : Visual Studio ソリューションに含まれていない実行可能ファイルをデバッグする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトに含まれない実行可能ファイルをデバッグすることが必要な場合もあります。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の外部で作成された実行可能ファイルや、他の人から受け取った実行可能ファイルなどがその例です。  
  
 この問題を解決するには、通常、Visual Studio 外部の実行可能ファイルを起動して、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] デバッガーを使用してそのファイルにアタッチします。  詳細については、「[実行中のプロセスへのアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)」を参照してください。  
  
 アプリケーションへのアタッチは、一部を手動で実行する必要があります。この処理には数秒かかります。  アプリケーションの起動時に発生する問題をデバッグする場合は、このわずかな遅延のため、アタッチが役に立ちません。  また、ユーザー入力を待たず、すぐに終了するプログラムをデバッグする場合は、アタッチしている時間がないこともあります。  [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] がインストールされている場合は、このようなプログラムの EXE プロジェクトを作成できます。  
  
### 既存の実行可能ファイルの EXE プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューの **\[開く\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
2.  **\[プロジェクトを開く\]** ダイアログ ボックスで、**\[ファイル名\]** ボックスの横のドロップダウン リストをクリックし、**\[すべてのプロジェクト ファイル\]** を選択します。  
  
3.  目的の実行可能ファイルを指定して **\[OK\]** をクリックします。  
  
     これにより、実行可能ファイルを格納する一時的なソリューションが作成されます。  
  
### Visual Studio ソリューションに実行可能ファイルをインポートするには  
  
1.  **\[ファイル\]** メニューの **\[プロジェクトの追加\]** をポイントし、**\[既存のプロジェクト\]** をクリックします。  
  
2.  **\[既存プロジェクトの追加\]** ダイアログ ボックスで、**\[ファイル名\]** ボックスの横のドロップダウン リストをクリックし、**\[すべてのプロジェクト ファイル\]** を選択します。  
  
3.  目的の実行可能ファイルを見つけ、選択します。  
  
4.  **\[OK\]** をクリックします。  
  
5.  **\[デバッグ\]** メニューの **\[開始\]** などの実行コマンドを選択することで、実行可能ファイルを起動します。  
  
    > [!NOTE]
    >  EXE プロジェクトをサポートしていないプログラミング言語もあります。  この機能を使用する必要がある場合は、[!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] をインストールしてください。  
  
     ソース コードなしで実行可能ファイルをデバッグする場合は、実行中の実行可能ファイルにアタッチするか、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソリューションに実行可能ファイルを追加するかにかかわらず、利用できるデバッグ機能が限られます。  実行可能ファイルが、互換性のある形式のデバッグ情報を持たずにビルドされていた場合、利用できる機能はさらに限られます。  ソース コードがある場合は、そのソース コードを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] にインポートして、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で実行可能ファイルのデバッグ ビルドを作成するのが最適です。  
  
## 参照  
 [デバッグの設定と準備](../debugger/debugger-settings-and-preparation.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [DBG Files](http://msdn.microsoft.com/ja-jp/91e449e9-8b65-4123-960f-2107cd1f1cfd)