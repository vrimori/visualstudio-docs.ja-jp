---
title: "方法: アクティビティ ログを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c27934d043a067f88bd9f47efe7d8f7972959e10
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-activity-log"></a>方法: アクティビティ ログを使用
Vspackage は、メッセージを動作状況ログを書き込むことができます。 この機能は、小売環境で Vspackage をデバッグするため便利です。  
  
> [!TIP]
>  アクティビティ ログは常にオンにします。 Visual Studio では、一般的な構成情報を持つ最初の 10 個のエントリと同様に、100 を最後のエントリのローリング バッファーが保持されます。  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>アクティビティ ログにエントリを書き込む  
  
1.  このコードを挿入、<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>メソッドまたはコンス トラクターは、VSPackage を除く他のメソッドで。  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     このコードを取得、<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>サービスおよびにキャスト、<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>インターフェイスです。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>現在のカルチャ コンテキストを使用して、動作状況ログに情報のエントリを書き込みます。  
  
2.  (通常コマンドが呼び出されるまたはウィンドウが開くとき)、VSPackage が読み込まれると、テキストが、動作状況ログに書き込まれます。  
  
### <a name="to-examine-the-activity-log"></a>アクティビティのログを確認するには  
  
1.  Visual Studio のデータのサブフォルダーに、動作状況ログが見つかりません: *%appdata%*\Microsoft\VisualStudio\15.0\ActivityLog.XML.  
  
2.  任意のテキスト エディターで、動作状況ログを開きます。 一般的なエントリを次に示します。  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 アクティビティ ログは、サービスであるためには、動作状況ログは、VSPackage のコンス トラクターで使用できません。  
  
 記述する前に、動作状況ログを取得する必要があります。 キャッシュしたり、将来使用するためのアクティビティ ログを保存しないでください。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Vspackage のトラブルシューティング](../extensibility/troubleshooting-vspackages.md)   
 [VSPackage](../extensibility/internals/vspackages.md)
