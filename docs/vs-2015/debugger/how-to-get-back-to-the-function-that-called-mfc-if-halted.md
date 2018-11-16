---
title: '方法: 停止した場合に MFC を呼び出した関数に戻る |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.mfc
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f42e7440775f76764b7bd11399f6507f92c377a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723416"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>方法 : 停止した場合に MFC を呼び出した関数に戻る
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

注]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、[ツール] メニューの [設定のインポートとエクスポート] をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 使用した場合、**中断**コマンドを**デバッグ**プログラムを停止するにはメニューと mfc では、最終的には、コードに問題があることを確認する呼び出し履歴 ウィンドウを使用して、関数に戻ることができます。 詳細については、次を参照してください。[方法: 呼び出し履歴 ウィンドウを使用して、](../debugger/how-to-use-the-call-stack-window.md)します。  
  
 コードがメッセージ ポンプ内で中断する場合があります。 この場合、呼び出し履歴にユーザー コードは存在しません。 この問題を回避するの代わりに (場合によって条件とヒット カウント用) でブレークポイントを使用することができます、**中断**コマンド。 詳細については、次を参照してください。[ブレークポイントとトレース ポイント](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583))。  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>MFC の呼び出し元の関数を参照するには  
  
-   使用して、**呼び出し履歴**ウィンドウ。  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグに関する Faq](../debugger/debugging-native-code-faqs.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)



