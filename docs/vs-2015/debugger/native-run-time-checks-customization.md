---
title: ネイティブ ランタイム チェックのカスタマイズ |Microsoft Docs
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
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 396778e87732d73462a7ecc2a420ea22a00936b1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856602"
---
# <a name="native-run-time-checks-customization"></a>ネイティブ ランタイム チェックのカスタマイズ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

コンパイルするとき **/RTC** (実行時チェック) を使用して、または、`runtime_checks`プラグマ、C ランタイム ライブラリはネイティブ ランタイム チェックを提供します。 ランタイム チェックのカスタマイズが必要になる場合があります。次に例を示します。  
  
- ランタイム チェック メッセージを既定とは異なるファイルや出力先に転送する。  
  
- サードパーティ デバッガーでのランタイム チェック メッセージの出力先を指定する。  
  
- C ランタイム ライブラリのリリース バージョンでコンパイルされたプログラムからのランタイム チェック メッセージを報告する。 ライブラリのリリース バージョンでは、ランタイム エラーの報告に `_CrtDbgReportW` は使用されません。 代わりに、表示、 **Assert**  ダイアログ ボックスの各実行時エラーが発生します。  
  
  ランタイム エラー チェックをカスタマイズするには、次の方法があります。  
  
- ランタイム エラー レポート関数の記述 詳細については、次を参照してください。[方法: 実行時エラー レポート関数を記述](../debugger/how-to-write-a-run-time-error-reporting-function.md)します。  
  
- エラー メッセージ出力先のカスタマイズ  
  
- ランタイム チェック エラーに関する情報のクエリ  
  
## <a name="customize-the-error-message-destination"></a>エラー メッセージ出力先のカスタマイズ  
 エラー レポートに `_CrtDbgReportW` を使用する場合は、`_CrtSetReportMode` を使用してエラー メッセージの出力先を指定できます。  
  
 カスタムのレポート関数を使用している場合、エラーとレポートの種類を関連付けるには、`_RTC_SetErrorType` を使用します。  
  
## <a name="query-for-information-about-run-time-checks"></a>ランタイム チェック情報のクエリ  
 `_RTC_NumErrors` は、ランタイム エラー チェックで検出されたエラーの種類の数を返します。 各エラーの簡単な説明を取得するには、0 ～ `_RTC_NumErrors` の戻り値をループし、各ループで `_RTC_GetErrDesc` に反復値を渡すことができます。 詳細については、次を参照してください。 [_RTC_NumErrors](http://msdn.microsoft.com/library/7e82adae-38e2-4f8b-bc0b-37bda8109fd1)と[_RTC_GetErrDesc](http://msdn.microsoft.com/library/7994ec2b-5488-4fd4-806d-a166c9a9f927)します。  
  
## <a name="see-also"></a>関連項目  
 [方法: ネイティブ ランタイム チェックを使用](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [_CrtDbgReport、_CrtDbgReportW](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc)





