---
title: "入れ子になったプロジェクトに対するコマンド処理を実装します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コマンドの処理を実装する、入れ子になったプロジェクト"
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 入れ子になったプロジェクトに対するコマンド処理を実装します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IDE では入れ子になったプロジェクトに <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> と <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> のインターフェイスを通じて渡される親プロジェクトではコマンドはフィルター処理またはオーバーライドするコマンドを渡すことができます。  
  
> [!NOTE]
>  通常は親プロジェクトで処理される唯一のコマンドでフィルター処理できます。  IDE で処理 **Build** と **Deploy** などのコマンドはフィルター処理できません。  
  
 次の手順ではコマンドの処理を実行するプロセスについて説明します。  
  
## 手順  
  
#### コマンドの処理を実行します。  
  
1.  入れ子になったユーザーがプロジェクト内に入れ子になったプロジェクトまたはノードを選択する場合 :  
  
    1.  IDE で <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> のメソッドを呼び出します。  
  
     または  
  
    1.  コマンドがソリューション エクスプローラーのショートカット メニュー コマンドなどの階層\] ウィンドウにIDE を呼び出すとプロジェクトの親 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> のメソッドを起きたら。  
  
2.  親プロジェクトは親プロジェクトをコマンドをフィルター処理するかどうかを確認するに `QueryStatus` に`pguidCmdGroup` と `prgCmds` のような渡すパラメーターをチェックできます。  コマンドをフィルター処理する親プロジェクトを実行したときに設定する必要があります :  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     その親プロジェクトは `S_OK` を返す必要があります。  
  
     親プロジェクトをコマンドをフィルター処理`S_OK` を返す必要があります。  この場合子プロジェクトに自動的にコマンドをルーティングします。  
  
     親プロジェクトはプロジェクトにコマンドをルーティングする必要はありません。  IDE ではこのタスクを実行します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [コマンド、メニューのおよびツールバー](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [入れ子のプロジェクト](../../extensibility/internals/nesting-projects.md)