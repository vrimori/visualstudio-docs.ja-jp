---
title: マネージ コードの複数のスレッドを管理する |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a33b17ddc0eb2d6169761260905b9bf056a4c55e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802357"
---
# <a name="managing-multiple-threads-in-managed-code"></a>マネージド コードの複数のスレッドを管理する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

非同期メソッドの呼び出しまたは Visual Studio の UI スレッド以外のスレッドで実行される操作がマネージ VSPackage 拡張機能の場合は、以下のガイドラインに従ってください。 保持できます UI スレッド応答性の高い作業を完了する別のスレッドで待機する必要がないです。 行うことができます、コードをより効率的な余分なスレッドがスタックの領域を占有する必要がないためより信頼性が高く、デッドロックやハングを回避するためのデバッグを簡単に行うことができます。  
  
 一般に、別のスレッドに UI スレッドから切り替えることができますまたはその逆です。 メソッドが戻るときに、現在のスレッドは、その最初の呼び出し元スレッドです。  
  
> [!IMPORTANT]
>  次のガイドラインで Api を使用して、<xref:Microsoft.VisualStudio.Threading>具体的には、名前空間、<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>クラス。 この名前空間の Api は、の新しい[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]します。 インスタンスを取得することができます、<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>から、<xref:Microsoft.VisualStudio.Shell.ThreadHelper>プロパティ`ThreadHelper.JoinableTaskFactory`します。  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>バック グラウンド スレッド UI スレッドからに切り替える  
  
1.  UI スレッドを使用している場合に、バック グラウンド スレッドで非同期作業を行うには、Task.Run() を使用します。  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2.  UI スレッドを使用しているし、使用して、バック グラウンド スレッドで作業を実行している間に同期的にブロックする場合、<xref:System.Threading.Tasks.TaskScheduler>プロパティ`TaskScheduler.Default`内<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
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
  
1.  バック グラウンド スレッドにいるし、使用して、UI スレッドで何かを実行するかどうか<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     使用することができます、<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>メソッドを UI スレッドに切り替えます。 このメソッドは、現在の非同期メソッドの継続で UI スレッドにメッセージを投稿し、適切な優先順位を設定して、デッドロックを回避するためにスレッドのフレームワークの残りの部分とも通信。  
  
     使用できますが、バック グラウンド スレッドは、メソッドは非同期非同期にできない場合は、`await`構文を使用した作業をラップすることによって、UI スレッドに切り替える<xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>、この例のように。  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```

