---
title: "方法: テストし、ビジュアライザーのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57e4387fad4a750af26245febe5d9573d43deccc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-test-and-debug-a-visualizer"></a>方法 : ビジュアライザーをテストおよびデバッグする
ビジュアライザーを記述したら、デバッグとテストを行う必要があります。  
  
 テスト方法の 1 つとして、ビジュアライザーを Visual Studio にインストールし、デバッガー ウィンドウから呼び出します。 (を参照してください[する方法: ビジュアライザーをインストール](../debugger/how-to-install-a-visualizer.md))。この方法では、Visual Studio のインスタンスをもう 1 つ使用してビジュアライザーの追加とデバッグを行う必要があります。デバッグ対象のビジュアライザーは、デバッガーの最初のインスタンス内で実行されます。  
  
 ビジュアライザーのデバッグをより簡単に行うには、ビジュアライザーをテスト ドライバーから実行します。 ビジュアライザー Api では、簡単と呼ばれるこのようなドライバーを作成、*ビジュアライザー開発ホスト*です。  
  
### <a name="to-create-a-visualizer-development-host"></a>ビジュアライザー開発ホストを作成するには  
  
1.  デバッガー側のクラスに <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> オブジェクトを作成する静的メソッドを含め、その Show メソッドを呼び出します。  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     ホストの構築に使用するパラメーターは、ビジュアライザーに表示されるデータ オブジェクト (`objectToVisualize`) とデバッガー側のクラスの型です。  
  
2.  `TestShowVisualizer` を呼び出すための次のステートメントを追加します。 クラス ライブラリにビジュアライザーを作成した場合は、そのクラス ライブラリを呼び出す実行可能ファイルを作成し、このステートメントをその実行可能ファイルに配置します。  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     完全な例では、次を参照してください。[チュートリアル: c# でビジュアライザーを記述する](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)です。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: ビジュアライザーを記述する (C#)](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [方法: ビジュアライザーをインストール](../debugger/how-to-install-a-visualizer.md)   
 [カスタム ビジュアライザーを作成する](../debugger/create-custom-visualizers-of-data.md)