---
title: "方法: アクティビティ ログを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c9df048a49580f3526b48e29041ef3758722ed27
ms.openlocfilehash: dc821f22a04432989a2edb68c483d298ffcf0eb7
ms.lasthandoff: 05/03/2017

---
# <a name="how-to-use-the-activity-log"></a>方法: アクティビティ ログを使用
Vspackage は、メッセージを動作状況ログを書き込むことができます。 この機能は、小売環境で Vspackage をデバッグするため便利です。  
  
> [!TIP]
>  アクティビティ ログは常にオンにします。 Visual Studio では、一般的な構成情報を持つ最初の 10 個のエントリと同様に、100 を最後のエントリのローリング バッファーが保持されます。  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>アクティビティ ログにエントリを書き込む  
  
1.  < Xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A > メソッドや VSPackage コンス トラクターを除く他のメソッドでは、このコードを挿入します。  
  
    ```c#  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     このコードは、< xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog > サービスを取得し、< xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog > インターフェイスにキャストします。 < xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A > は、現在のカルチャ コンテキストを使用して、動作状況ログに情報のエントリを書き込みます。  
  
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
  
## <a name="see-also"></a>関連項目  
 < xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog >   
 < xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE >   
 [Vspackage のトラブルシューティング](../extensibility/troubleshooting-vspackages.md)   
 [VSPackage](../extensibility/internals/vspackages.md)

