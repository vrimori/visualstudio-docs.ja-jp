---
title: '方法: アクティビティ ログを使用して |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6200c5e71054c6132d9239769d354bfd32703fb0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-the-activity-log"></a>方法: アクティビティ ログを使用
Vspackage は、メッセージを動作状況ログを書き込むことができます。 この機能は、小売環境で Vspackage をデバッグするため便利です。  
  
> [!TIP]
>  アクティビティ ログは常にオンにします。 Visual Studio では、一般的な構成情報を持つ最初の 10 個のエントリと同様に、最新の 100 個のエントリのローリング バッファーが保持されます。  
  
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
  
     このコードを取得、<xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>サービスおよびにキャスト、<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>インターフェイスです。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> 現在のカルチャ コンテキストを使用して、動作状況ログに情報のエントリを書き込みます。  
  
2.  (通常コマンドが呼び出されるまたはウィンドウが開くとき)、VSPackage が読み込まれると、テキストが、動作状況ログに書き込まれます。  
  
### <a name="to-examine-the-activity-log"></a>アクティビティのログを確認するには  
  
1.  Visual Studio と実行、 [/ログ](../ide/reference/log-devenv-exe.md)ActivityLog.xml をディスクに書き込むセッション中にコマンド ライン スイッチです。

2.  Visual Studio を閉じると、アクティビティのログ サブフォルダーにデータを探す Visual Studio: *%appdata%*\Microsoft\VisualStudio\15.0\ActivityLog.xml です。  
  
3.  任意のテキスト エディターで、動作状況ログを開きます。 一般的なエントリを次に示します。  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 アクティビティ ログは、サービスであるためには、動作状況ログは、VSPackage のコンス トラクターで使用できません。  
  
 記述する前に、動作状況ログを取得する必要があります。 キャッシュしたり、将来使用するためのアクティビティ ログを保存しないでください。  
  
## <a name="see-also"></a>関連項目
 [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Vspackage のトラブルシューティング](../extensibility/troubleshooting-vspackages.md)   
 [VSPackage](../extensibility/internals/vspackages.md)
