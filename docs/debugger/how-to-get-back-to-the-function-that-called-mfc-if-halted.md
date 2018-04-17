---
title: '方法: 停止した場合は、MFC を呼び出した関数に戻る |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba928ae40c02b16be62d60f8fd602f5a0f2ca294
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>方法 : 停止した場合に MFC を呼び出した関数に戻る
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、[ツール] メニューの [設定のインポートとエクスポート] をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
 使用した場合、**中断**コマンドを**デバッグ** メニューのプログラムを停止するようと MFC では、最終的に実行され、コードに問題があることを確認して、関数に戻るに呼び出し履歴 ウィンドウを使用することができます。 詳細については、次を参照してください。[する方法: 呼び出し履歴 ウィンドウを使用して](../debugger/how-to-use-the-call-stack-window.md)です。  
  
 コードがメッセージ ポンプ内で中断する場合があります。 この場合、呼び出し履歴にユーザー コードは存在しません。 この問題を避けるためには、代わりに (おそらく、ブレークポイントのヒット カウント) を使用することができます、**中断**コマンド。 詳細については、次を参照してください。[ブレークポイントとトレース ポイント](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583))。  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>MFC の呼び出し元の関数を参照するには  
  
-   使用して、**呼び出し履歴**ウィンドウです。  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグに関する Faq](../debugger/debugging-native-code-faqs.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)