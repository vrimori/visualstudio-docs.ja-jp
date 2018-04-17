---
title: '方法: マネージ コードの複数のスレッドを管理する |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c0888a0f65f36d624deffac60ceee032d3f3d13a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>方法: マネージ コードの複数のスレッドを管理します。
非同期メソッドを呼び出すか、Visual Studio の UI スレッド以外のスレッドで実行される操作するマネージ VSPackage 拡張機能があれば、以下のガイドラインに従ってください。 おくと、UI スレッド応答性の高い作業を完了する別のスレッドで待機する必要がないためです。 ことができます、コードをより効率的なスタック領域を占有する追加のスレッドがないためより信頼性が高く、デッドロックやハングを回避するため、デバッグを簡単に行うことができます。  
  
 一般に、UI スレッドからに切り替える別のスレッド、またはその逆です。 メソッドが戻るとき、現在のスレッドは、その最初の呼び出し元スレッドです。  
  
> [!IMPORTANT]
>  次のガイドラインで Api を使用して、<xref:Microsoft.VisualStudio.Threading>具体的には、名前空間、<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>クラスです。 この名前空間の Api が追加されて[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]です。 インスタンスを取得することができます、<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>から、<xref:Microsoft.VisualStudio.Shell.ThreadHelper>プロパティ`ThreadHelper.JoinableTaskFactory`です。  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>UI スレッドからバック グラウンド スレッドに切り替える  
  
1.  UI スレッドでは、バック グラウンド スレッドで非同期操作を実行する場合は、Task.Run() を使用します。  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you're on a separate thread.  
    });  
    // Now you're back on the UI thread.  
  
    ```  
  
2.  UI スレッドでは、同期的にブロックを使用して、バック グラウンド スレッドで作業を実行しているときにする場合、<xref:System.Threading.Tasks.TaskScheduler>プロパティ`TaskScheduler.Default`内<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>バック グラウンド スレッドから UI スレッドへの切り替え  
  
1.  バック グラウンド スレッドでしているしを使用して、UI スレッドで何かを実行するかどうかは<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     使用することができます、 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> UI スレッドに切り替えるにはメソッドです。 このメソッドは、UI スレッドと現在の非同期メソッドの continuation にメッセージをポストし、正しいの優先順位を設定し、デッドロックを回避するために、スレッド フレームワークの残りの部分とも通信します。  
  
     バック グラウンド スレッド メソッドは非同期とすることはできません、非同期場合、引き続き使用できます、`await`構文を使用した作業をラップすることによって、UI スレッドに切り替えるに<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>、この例のようにします。  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```