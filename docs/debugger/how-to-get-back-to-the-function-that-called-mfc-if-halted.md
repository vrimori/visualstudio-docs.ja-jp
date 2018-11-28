---
title: '方法: 停止した場合に MFC を呼び出した関数に戻る |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: af8856a4356a829b37a4a624b86f7b29dd965f9c
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389459"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>方法 : 停止した場合に MFC を呼び出した関数に戻る

> [!NOTE]
> 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、次を参照してください。[設定にリセット](../ide/environment-settings.md#reset-settings)します。

[デバッグ] **メニューの [中断]** コマンドでプログラムを中断した場合に MFC 内で実行が停止されたとします。そのとき、問題が自分自身で作成したコードにあることが明らかな場合は、[呼び出し履歴] ウィンドウを使用することにより、呼び出し元の関数に戻ることができます。 詳細については、次を参照してください。[方法: 呼び出し履歴 ウィンドウを使用して、](../debugger/how-to-use-the-call-stack-window.md)します。

コードがメッセージ ポンプ内で中断する場合があります。 この場合、呼び出し履歴にユーザー コードは存在しません。 この問題を回避するには、[中断]** コマンドではなく、ブレークポイントを使用する必要があります。適宜、条件とヒット カウントを組み合わせて使用します。 詳細については、「 [Breakpoints and Tracepoints](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)」を参照してください。

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>MFC の呼び出し元の関数に移動します

-   [呼び出し履歴]** ウィンドウを使用します。

## <a name="see-also"></a>関連項目

- [ネイティブ コードのデバッグに関する FAQ](../debugger/debugging-native-code-faqs.md)
- [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)