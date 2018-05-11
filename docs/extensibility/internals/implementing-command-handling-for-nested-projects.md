---
title: プロジェクトのコマンドの処理を実装する入れ子になった |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f3f02752fad6932bac90597d56f27257e78b84cd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-command-handling-for-nested-projects"></a>入れ子になったプロジェクトの処理コマンドの実装
IDE が経由で渡されるコマンドを渡すことができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>と<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>入れ子になったプロジェクト、または親プロジェクトへのインターフェイスのフィルター処理または、コマンドを無視できます。  
  
> [!NOTE]
>  通常、親プロジェクトによって処理されるコマンドのみをフィルター処理することができます。 などのコマンド**ビルド**と**展開**によって処理される、IDE をフィルター処理することはできません。  
  
 次の手順では、コマンドの処理を実装するためのプロセスについて説明します。  
  
## <a name="procedures"></a>手順  
  
#### <a name="to-implement-command-handling"></a>コマンドの処理を実装するには  
  
1.  選択すると、ユーザー、入れ子になったプロジェクトまたはノードの入れ子にされたプロジェクト。  
  
    1.  IDE の呼び出し、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドです。  
  
     または  
  
    1.  ソリューション エクスプ ローラーで、ショートカット メニュー コマンドなどの階層ウィンドウで、コマンドが作成された場合は、IDE によって呼び出さ、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>プロジェクトの親のメソッドです。  
  
2.  渡されるパラメーターを調べることができます、親プロジェクト`QueryStatus`など`pguidCmdGroup`と`prgCmds`が親プロジェクトが、コマンドのフィルターを適用する必要があるかどうかを決定します。 コマンドをフィルター処理には、親プロジェクトが実装されている場合、これを設定する必要があります。  
  
    ```  
    prgCmds[0].cmdf = OLECMDF_SUPPORTED;  
    // make sure it is disabled  
    prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;  
    ```  
  
     親プロジェクトを返す必要があります`S_OK`です。  
  
     親プロジェクトのコマンドは、フィルター処理しないかどうか、これだけを返します`S_OK`です。 ここでは、IDE は、子プロジェクトに対して、コマンドを自動的にルーティングします。  
  
     親プロジェクトは、子プロジェクトに対して、コマンドをルーティングする必要はありません。 IDE では、このタスクを実行.  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [コマンド、メニューのおよびツールバー](../../extensibility/internals/commands-menus-and-toolbars.md)   
 [入れ子になったプロジェクト](../../extensibility/internals/nesting-projects.md)