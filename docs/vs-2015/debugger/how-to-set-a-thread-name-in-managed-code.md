---
title: '方法: マネージ コードのスレッド名を設定 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Thread.Name property
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c0c4d74a-0314-4b71-81c9-b0b019347ab8
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a921fcdcd19114842e026f1ebc3bcb699e200f89
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256105"
---
# <a name="how-to-set-a-thread-name-in-managed-code"></a>方法 : マネージド コードのスレッド名を設定する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

スレッド名の設定は、Visual Studio のどのエディションでも実行できます。 内のスレッドを追跡するために便利ですがスレッドの名前を付け、**スレッド**ウィンドウ。 **スレッド**ウィンドウが Visual Studio Express エディションで使用できない、スレッド名、Express edition ではほとんどのユーティリティを設定します。  
  
 マネージド コードのスレッド名を設定するには、<xref:System.Threading.Thread.Name%2A> プロパティを使用します。  
  
## <a name="example"></a>例  
  
```  
Public Class Needle  
    ' This method will be called when the thread is started.  
    Sub Baz()  
        Console.WriteLine("Needle Baz is running on another thread")  
    End Sub  
End Class  
  
Sub Main()  
    Console.WriteLine("Thread Simple Sample")  
    Dim oNeedle As New Needle()  
   ' Create a Thread object.   
    Dim oThread As New System.Threading.Thread(AddressOf oNeedle.Baz)  
    ' Set the Thread name to "MainThread".  
    oThread.Name = "MainThread"  
    ' Starting the thread invokes the ThreadStart delegate  
    oThread.Start()  
End Sub  
```  
  
## <a name="see-also"></a>関連項目  
 [マルチ スレッド アプリケーションをデバッグします。](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [方法 : ネイティブ コードのスレッド名を設定する](../debugger/how-to-set-a-thread-name-in-native-code.md)



