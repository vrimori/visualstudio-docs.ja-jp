---
title: "C# デバッグ構成のプロジェクト設定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "デバッグ ビルド, プロジェクト設定"
  - "デバッグ構成, C#"
  - "デバッグ構成, J#"
  - "デバッグ [C#], デバッガー設定"
  - "デバッグ [J#], デバッガー設定"
  - "プロジェクト構成, デバッグ"
  - "プロジェクト設定 [Visual Studio], デバッグ構成"
  - "プロジェクト [Visual Studio], デバッグ構成"
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C# デバッグ構成のプロジェクト設定
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

「**デバッグ構成とリリース構成**」でも説明されているように、C\# デバッグ構成のプロジェクト設定は [&#91;プロパティ ページ&#93;](../debugger/how-to-set-debug-and-release-configurations.md) ウィンドウで変更できます。  次の表は、**\[プロパティ ページ\]** ウィンドウのデバッガー関連の設定の場所を示しています。  
  
> [!WARNING]
>  このトピックは Windows ストア アプリには適用されません。  「[デバッグ セッションの開始 \(VB、C\#、C\+\+、および XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)」を参照してください。  
  
##  <a name="BKMK_Debug_tab"></a> \[デバッグ\] タブ  
  
|**設定**|**説明**|  
|------------|------------|  
|**構成**|アプリケーションをコンパイルするためのモードを設定します。  **\[アクティブ \(Debug\)\]**、**\[Debug\]**、**\[Release\]**、**\[すべての構成\]** から選択します。|  
|**開始動作**|\[デバッグ\] メニューの \[開始\] を選択したときに発生するアクションを指定します。<br /><br /> -   既定値は **\[プロジェクトの開始\]** で、デバッグのスタートアップ プロジェクトを起動します。  詳細については、「[スタートアップ プロジェクトの選択](http://msdn.microsoft.com/ja-jp/222e3f32-a6fe-4941-bf37-6b2a921129fd)」を参照してください。<br />-   **\[外部プログラムの開始\]** では、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトに含まれないプログラムを起動してアタッチできます。  詳細については、「[実行中のプログラムへのアタッチ](http://msdn.microsoft.com/ja-jp/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)」を参照してください。<br />-   **\[ブラウザーを開始時に使用する URL\]** は、Web アプリケーションのデバッグを有効にします。|  
|**\[コマンド ライン引数\]**|デバッグするプログラムのコマンド ライン引数を指定します。  コマンド名は、\[外部プログラムの開始\] に指定されたプログラム名です。  \[開始動作\] が \[URL の開始\] に設定されている場合、コマンド ライン引数は指定できません。|  
|**作業ディレクトリ**|デバッグするプログラムの作業ディレクトリを指定します。  [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] では、作業ディレクトリはアプリケーションが起動されるディレクトリであり、既定では \\bin\\debug です。|  
|**\[リモート コンピューターの使用\]**|アプリケーションがデバッグの目的で実行されるリモート コンピューターの名前、または [Msvsmon サーバー名](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md)です。  リモート コンピューター上の EXE ファイルの場所は、\[構成プロパティ\] フォルダー、\[ビルド\] カテゴリ内の \[出力パス\] プロパティで指定します。  また、EXE ファイルがリモート コンピューターの共有ディレクトリにあることも必要です。|  
|**\[アンマネージ コード デバッグを有効にする\]**|マネージ アプリケーションからネイティブ \(アンマネージ\) Win32 コードの呼び出しをデバッグできます。|  
|**\[SQL Server デバッグを有効にする\]**|SQL Server データベース オブジェクトのデバッグを許可します。|  
  
##  <a name="BKMK_Build_tab"></a> \[ビルド\] タブ  
  
|設定|説明|  
|--------|--------|  
|**条件付きコンパイル シンボル:**|定数 DEBUG および定数 TRACE をここで定義します。<br /><br /> これらの定数により、[Debug クラス](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.aspx)と [Trace クラス](https://msdn.microsoft.com/en-us/library/system.diagnostics.trace.aspx)の条件付きコンパイルが有効になります。  これらの定数を定義すると、Debug クラスと Trace クラスのメソッドは[出力ウィンドウ](../ide/reference/output-window.md)に出力を生成します。  これらの定数を定義しない場合、Debug クラスと Trace クラスのメソッドはコンパイルされず、出力も生成されません。<br /><br /> -   DEBUG は、通常、プログラムのデバッグ バージョンで定義され、リリース バージョンでは定義されません。<br />-   TRACE は、通常、デバッグ バージョンとリリース バージョンの両方で定義されます。|  
|**コードの最適化**|デバッグ バージョンでは、最適化されたコードにだけ現れるバグを見つけた場合に限って、この設定をオンにすることをお勧めします。  最適化されたコードは、命令がソース ウィンドウのステートメントに直接対応していないため、デバッグが困難です。|  
|**\[出力パス\]**|通常は、デバッグ用の bin\\Debug に設定します。|  
  
## 参照  
 [デバッグの設定と準備](../debugger/debugger-settings-and-preparation.md)