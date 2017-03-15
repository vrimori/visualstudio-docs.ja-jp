---
title: "方法: マネージ コードの複数のスレッドを管理する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 7
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
ms.sourcegitcommit: 477f57bbca9c49e7d7d13155fc1f6e55ee4667a8
ms.openlocfilehash: 417dc6e5285859424dfa3b482a90f1a141cff163
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>方法: マネージ コードの複数のスレッドを管理します。
非同期メソッドを呼び出してまたは Visual Studio の UI スレッド以外のスレッドで実行される操作をマネージ VSPackage 拡張機能があれば、次のガイドラインに従ってください。 おくと、UI スレッド応答性の高い作業を完了する別のスレッドで待機する必要がないためです。 コードも容易より効率的なスタック領域を占有する追加のスレッドがないため、信頼性を高めて、デッドロックやハングを避けるために、デバッグを容易に行うことができます。  
  
 別のスレッドに UI スレッドから切り替えることができます一般に、またはその逆です。 メソッドが戻るとき、現在のスレッドは、その最初の呼び出し元スレッドです。  
  
> [!IMPORTANT]
>  次のガイドラインは、<xref:Microsoft.VisualStudio.Threading>名前空間、具体的には、<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>クラス</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory></xref:Microsoft.VisualStudio.Threading>で、Api を使用します。 この名前空間に含まれる Api は、新機能[!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]です。 インスタンスを取得することができます、<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>から、<xref:Microsoft.VisualStudio.Shell.ThreadHelper>プロパティ`ThreadHelper.JoinableTaskFactory`</xref:Microsoft.VisualStudio.Shell.ThreadHelper></xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>。  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>UI スレッドから、バック グラウンド スレッドに切り替える  
  
1.  UI スレッドを使用している場合に、バック グラウンド スレッドで非同期の作業を行うには、Task.Run() を使用します。  
  
    ```c#  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2.  UI スレッドを使用しているし、バック グラウンド スレッドで使用する作業を行うときに同期的にブロックする場合、<xref:System.Threading.Tasks.TaskScheduler>プロパティ`TaskScheduler.Default` <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>::</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>内</xref:System.Threading.Tasks.TaskScheduler>  
  
    ```c#  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>バック グラウンド スレッドから UI スレッドへの切り替え  
  
1.  バック グラウンド スレッドで UI スレッドで何かの操作を実行する場合は、 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>::</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>を使用します。  
  
    ```c#  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     使用することができます、<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>メソッドを UI スレッドに切り替える</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>。 このメソッドは、現在の非同期メソッドの継続で UI スレッドにメッセージをポストし、適切な優先順位を設定し、デッドロックを回避するのには、スレッド処理のフレームワークの残りの部分とも通信します。  
  
     バック グラウンド スレッド メソッドは非同期と非同期させることはできません場合、引き続き使用できます、`await`構文を使用した作業をラップすることによって、UI スレッドに切り替える<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>この例のように、:</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>  
  
    ```c#  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
