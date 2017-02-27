---
title: "方法: 動作状況ログの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vspackage のデバッグ"
  - "Vspackage のトラブルシューティング"
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# 方法: 動作状況ログの使用
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackages には、メッセージを動作状況ログに書き込むことができます。 この機能は、小売環境である Vspackage をデバッグするため便利です。  
  
> [!TIP]
>  アクティビティ ログは常にオンにします。 Visual Studio では、一般的な構成情報がある、最初の 10 個のエントリと同様に 100 を最後のエントリのローリング バッファーを保持します。  
  
### アクティビティ ログにエントリを書き込む  
  
1.  このコードを挿入、 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> メソッドまたはコンス トラクターは、VSPackage を除く、他のメソッドで。  
  
    ```c#  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     このコードを取得、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> サービスおよびにキャスト、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> インターフェイスです。<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> 現在のカルチャのコンテキストを使用して、動作状況ログに情報のエントリを書き込みます。  
  
2.  \(通常、コマンドが呼び出されたウィンドウが開かれた\) 場合、VSPackage が読み込まれると、テキストは、動作状況ログに書き込まれます。  
  
### アクティビティのログを調べます  
  
1.  Visual Studio のデータのサブフォルダーで、動作状況ログを確認します *%appdata%*\\Microsoft\\VisualStudio\\14.0\\ActivityLog.XML.。  
  
2.  任意のテキスト エディターで、動作状況ログを開きます。 一般的なエントリを次に示します。  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## 信頼性の高いプログラミング  
 アクティビティ ログは、サービスなので、動作状況ログの内容は VSPackage コンス トラクターで使用可能なです。  
  
 書き込む直前に、動作状況ログを取得する必要があります。 キャッシュまたは将来使用するためのアクティビティ ログを保存しないでください。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Vspackage のトラブルシューティング](../extensibility/troubleshooting-vspackages.md)   
 [Vspackages にあります。](../extensibility/internals/vspackages.md)